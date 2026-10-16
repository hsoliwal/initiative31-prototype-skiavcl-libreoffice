# Selected inherited VCL and Skia contracts

[Start here](START_HERE.md) · [Module index](MODULE_INDEX.md) · [Experimental bridge](PROTOTYPE_CONTRACTS.md) · [Coverage](COVERAGE.md)

## Evidence boundary

All source links on this page are pinned to the fork's `master` baseline
`38f3847c224e4d735a199e596b11b0a1cf9488e5`. These are inherited LibreOffice
facilities, not M3 implementations or capabilities introduced by this fork.
This is a selected contract review, not documentation of every VCL class,
platform backend, rendering operation, or namespace. Native compilation,
automated tests, graphics-driver behavior, and GUI execution were not run.

## VCL module and platform boundary

The [VCL README](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/README.md)
assigns VCL widget/windowing, OS abstraction, and rendering responsibilities.
Its `SalInstance` explanation describes the platform gateway for creating
frames, virtual devices, printers, timers, mutexes, drag-and-drop objects, and
event-loop services. A renderer supplies only part of that boundary.

[`Module_vcl.mk`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/Module_vcl.mk)
registers `Library_vcl`, UI configuration, resource packages, test groups,
conditional backend libraries, and demonstrations. Distinct switches select
GTK3/GTK4, Qt5/Qt6, KF5/KF6, GTK3/KDE5, generic X11, Windows, and macOS targets;
platform, headless, dynamic-loading, cross-compiling, and build-type conditions
also matter. A source directory's presence does not mean its backend is selected.

[`Library_vcl.mk`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/Library_vcl.mk)
places `skia/salbmp`, `skia/zone`, and `skia/gdiimpl` plus the `skia` external
dependency behind a `SKIA` build-type condition in its non-`DISABLE_GUI` branch.
Platform-specific objects have additional guards. Build inclusion, backend
preparation, enablement, and successful GPU use are separate questions.

## Application and object lifetime

### Minimal inherited application

The complete [`minvcl.cxx`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/workben/minvcl.cxx)
body demonstrates the sequence: create `TheApplication`; bootstrap a UNO
component context and process service factory; set the configured system
language; initialize VCL; create/show a `WorkWindow`; run `Execute()`; dispose
the member window; terminate the framework desktop; deinitialize VCL; clear the
process service factory. This sequence owns process-wide infrastructure as well
as a window. It is not a declaration that every call can be independently
repeated or moved to an arbitrary Java thread.

### VclPtr versus disposal

The full [`include/vcl/vclptr.hxx`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/include/vcl/vclptr.hxx)
body and [lifecycle notes](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/README.lifecycle.md)
distinguish a retained reference from the disposal of the referenced object.

| Surface | Contract visible in the header | Consequence |
| --- | --- | --- |
| `VclPtr<T>` | Wraps `rtl::Reference<T>`; compile-time constraints permit incomplete types or types derived from `VclReferenceBase` | It is a reference wrapper, not an independent application/session owner |
| `VclPtr<T>::Create(args...)` | Constructs `T`, adopts its initial reference with `SAL_NO_ACQUIRE`, and returns a wrapper | The caller still needs the appropriate disposal ownership protocol |
| `clear()` / `reset()` | Clear the inner reference | These bodies do not call `disposeOnce()` |
| `disposeAndClear()` | Moves the inner reference into a temporary, leaves this wrapper empty, and invokes `disposeOnce()` if non-null | Keeps the object alive while disposal runs; other references are not automatically cleared |
| `ScopedVclPtr<T>` destructor | Calls `disposeAndClear()` | Scoped destruction includes disposal, unlike merely releasing a plain `VclPtr` reference |
| `disposeAndReset(T*)` | Disposes the old reference before assigning a different pointer; same-pointer assignment is skipped | Reassignment is an ownership event, not just a raw pointer store |
| `VclPtrInstance<T>` / `ScopedVclPtrInstance<T>` | Construction helpers; inherited `Create` is deliberately deleted | Do not assume the two helper families have identical end-of-scope semantics |

Debug-only checks in the plain wrapper's destructor are conditional on
`DBG_UTIL` and non-Windows builds. They check lifetime/disposal assumptions;
their presence is not a release-build enforcement guarantee. The header's
class comment describes window subclasses, while the actual template constraint
uses `VclReferenceBase`; the lifecycle test also instantiates `VirtualDevice`.
Keep the implementation and tested usages in view rather than reducing the
contract to the shorter comment.

The [scheduler notes](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/README.scheduler.md)
and VCL README explain event-loop and SolarMutex constraints. They are
inherited design guidance, not proof that the experimental JNI entry point
implements GUI-thread dispatch or safe callback reentrancy.

## Skia integration boundaries

| Boundary | Responsibility and source |
| --- | --- |
| `external/skia` | External dependency build/patch integration. Its [module](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/skia/Module_skia.mk) registers `UnpackedTarball_skia` and `Library_skia` |
| `vcl/skia` | VCL's use of Skia for drawing, bitmap handling, context sharing, and diagnostics. It is not the complete downloaded Skia source tree |
| `include/vcl/skia/SkiaHelper.hxx` | Exported helper declarations for enablement/logging, render-method selection, and cleanup, with feature guards |
| `vcl/inc/skia` | Internal integration declarations, including `utils.hxx`, bitmap/graphics implementations, and platform-specific headers; path inventory is complete, semantic review is selected |
| VCL platform implementations | Supply the backend/window context integration. Not every VCL backend supports Skia |

The [external README](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/skia/README)
identifies Skia's upstream and explains the tarball maintenance workflow.
[`UnpackedTarball_skia.mk`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/skia/UnpackedTarball_skia.mk)
consumes `SKIA_TARBALL` and applies the listed local patches, including the
shared-context patch. The downloaded archive's own packages and license
contents were not fetched or reviewed here. A patch listing is not a review of
each patch's behavior, a complete bill of materials, or a licensing conclusion.

### Selection is stateful

These observations come from the complete
[`SkiaHelper.cxx`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/skia/SkiaHelper.cxx)
body, the [public header](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/include/vcl/skia/SkiaHelper.hxx),
and the [internal utility declarations](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/inc/skia/utils.hxx).

1. Without `HAVE_FEATURE_SKIA`, `isVCLSkiaEnabled()` and
   `isAlphaMaskBlendingEnabled()` return false in this translation unit.
2. With Skia built, `prepareSkia(callback)` stores a GPU window-context creation
   callback and marks backend support. The first enablement evaluation checks
   that support and `SAL_DISABLESKIA`, then applies force/GL/enable options and
   the ordinary safe-mode branch. A selected enabled path initializes Skia and
   checks the device; it can start the watchdog and write crash-report state.
3. Enablement is cached through static variables. In particular, the cached
   return is `bForceSkia || bEnable`, whereas first evaluation returns `bRet`.
   Do not simplify this implementation into a universally enforced precedence
   table for contradictory force/disable/backend settings. The first-call and
   repeated-call paths need separate tests. No such tests were run here.
4. `SAL_SKIA` selects `raster`, or the platform-appropriate `metal`/`vulkan`
   branch. An unrecognized value reaches `abort()` when that selection path is
   evaluated. Bitmap-rendering mode chooses raster before reading this variable.
   Otherwise the configuration and compiled GPU support determine the initial
   selection. `renderMethodToUse()` performs one-time initialization.
5. Device/context failures can fall back to raster. Vulkan denylisting, Metal
   device/context checks, GPU-context creation, and offscreen-surface creation
   have different fallback paths. `SAL_FORCESKIA` is not a safe diagnostic
   shortcut and should not be used here to bypass a problematic renderer.

The inherited [variable reference](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/README.vars.md)
is an introduction. `SAL_USE_VCLPLUGIN` selects a VCL plugin;
`SAL_ENABLESKIA` requests Skia use; `SAL_SKIA` selects a drawing method.
Several settings are tested by presence, not by parsing a numeric Boolean.
Changing environment variables after initialization is not a supported
live-reconfiguration contract established by this source.

### Resource, failure, and concurrency details

| Selected helper | Contract and limit from the inspected body |
| --- | --- |
| `getSharedGrDirectContext()` | Asserts a non-raster method, reuses an existing context when available, or tries the registered callback once. It may return null and switch the method to raster; a caller cannot assume a GPU context always exists |
| `createSkSurface(width, height, type, alpha)` | Expects N32 or alpha-8 color type; uses raster for surfaces with both dimensions at most 32, otherwise tries the selected GPU path before raster fallback. If raster surface creation also fails, it aborts rather than returning a general recoverable error |
| `makeCheckedImageSnapshot(...)` | Asserts a non-null snapshot and aborts if it cannot obtain one; it is not an optional-result API |
| Image cache helpers | Cache `sk_sp<SkImage>` values by key, track estimated pixel cost, move hits to the front, and evict from the back to satisfy the configured size. `SAL_DISABLE_SKIA_CACHE` disables additions; this is not a proof of exact GPU memory accounting |
| `getSkImageChecksum(image)` | Caches checksums by image ID and requires accessible pixel data; it aborts when `peekPixels` fails. This is an image-data checksum, not a semantic-equivalence proof |
| `cleanup()` | Resets the shared window context, clears the image cache and its size, and resets the two cached blenders. It does not reset every static selection/cache variable, so it does not establish a full in-process restart protocol |
| `readLog()` / device diagnostics | Read or write the user-profile cache's `skia.log`; Vulkan diagnostics can record vendor/device/driver information and crash-report keys. Review logs before sharing |

[`SkiaZone`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/inc/skia/zone.hxx)
contains a `SolarMutexGuard` and participates in crash-zone tracking.
Its [`hardDisable()` implementation](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/skia/zone.cxx)
sets persistent `ForceSkiaRaster` configuration, commits it, and flushes the
configuration provider. This is an effectful recovery path, not merely a local
Boolean change. The source describes signal/watchdog invocation, but this review
does not independently verify signal-safety, race freedom, or thread safety of
all rendering and backend operations.

The [Skia README](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/skia/README)
contains historical guidance and some stale wording, including a sentence
listing Metal among unsupported alternatives despite its earlier Metal entry
and the conditional implementation. Preserve that history; use the pinned
source and actual configuration when reporting capabilities.

## Tests: what their source establishes

### VCL lifetime tests

[`CppunitTest_vcl_lifecycle.mk`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/CppunitTest_vcl_lifecycle.mk)
defines the inherited test integration. The full
[`lifecycle.cxx`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/qa/cppunit/lifecycle.cxx)
registers nine tests: casts, virtual devices, repeated disposal, isolated and
parented widgets, child disposal, selected post-disposal operations, leakage,
and UNO toolkit disposal. For example, the post-disposal test checks selected
window methods rather than asserting that every API remains valid after
disposal. The toolkit test checks `XComponent::dispose()` against the underlying
VCL object and then clears references. None of these tests exercises the
experimental `vcl4swt` exports.

### Skia tests can return without exercising Skia

[`CppunitTest_vcl_skia.mk`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/CppunitTest_vcl_skia.mk)
uses the non-headless VCL test integration; the module registers it only when
`SKIA` is in `BUILD_TYPE`. All 13 registered methods in
[`skia.cxx`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/qa/cppunit/skia/skia.cxx)
begin by returning if `isVCLSkiaEnabled()` is false. The file explicitly warns
about silent skipping. `testDrawDelayedScaleImage` also returns outside raster
mode because it tests raster-only caching.

The suite contains assertions for bitmap erase/shader behavior, alpha handling,
copy-on-write, scaling, checksums, and specific drawing regressions. Its presence
does not establish that those assertions executed in any reported run. A useful
future result must record the configured target, actual VCL backend, actual
Skia enablement and method, executed tests/skips, and environment. An aggregate
green result without backend evidence is insufficient for a Skia coverage claim.

## Remaining semantic work

The complete VCL tree inventory is not a complete API review. Rendering bodies
in `gdiimpl.cxx`/`salbmp.cxx`, platform integrations, every widget/header,
scheduler implementation, the downloaded Skia source, and all remaining test
semantics are unreviewed unless explicitly identified above. Inline source
comments are unchanged. Proposed M3 use of these boundaries would require its
own implementation and verification; this documentation does not demonstrate
an M3 kernel, deterministic promotion, or proof of contract preservation.
