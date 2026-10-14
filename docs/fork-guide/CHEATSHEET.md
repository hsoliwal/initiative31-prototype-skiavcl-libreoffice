# Quick start and command cheat sheet

[Start here](START_HERE.md) · [Examples](EXAMPLES.md) · [Root](../../README.md)

## First: choose a goal

- **Understand the architecture:** read the [VCL module README](../../vcl/README.md) and the [branch map](START_HERE.md#the-branch-map-matters).
- **Inspect the extraction experiment:** use the `vcl-4-swt` checkout below.
- **Build the historical source:** prepare an appropriate LibreOffice development environment first; see the build boundary below.
- **Find a ready-to-use SWT replacement:** this repository does not establish that outcome. Read the [final Initiative 31 report](https://github.com/swt-initiative31/documents/blob/main/report/overall_report.md) and follow the specific implementation it discusses.

## Quick start: inspect the experiment without building

Requires Git and a shell. The repository is large; a shallow, single-branch clone limits history, but does not make the source tree small.

```sh
git clone --depth 1 --single-branch --branch vcl-4-swt   https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice.git
cd initiative31-prototype-skiavcl-libreoffice
git branch --show-current
git rev-parse HEAD
git ls-files 'vcl4swt/*' 'VclUnoSwt/*' autogen.input
git show HEAD:VclUnoSwt/readme.txt
git show HEAD:autogen.input
```

At the documented experiment snapshot, the branch is `vcl-4-swt`, the revision is `19069d4d9992840913d2c085856a9af02420dc65`, and the two experiment directories are present. Future branch movement may produce a different commit; record it before comparing results.

## Source-inspection reference

| Goal | Command | Interpretation |
| --- | --- | --- |
| Confirm branch/revision | `git branch --show-current` and `git rev-parse HEAD` | Prevent confusing baseline and experiment results |
| Read historical Java instructions | `git show HEAD:VclUnoSwt/readme.txt` | Requires the experiment branch |
| Inspect bridge entry points | `git grep -n -E 'SAL_DLLPUBLIC_EXPORT\|JNIEXPORT' -- vcl4swt/src/api` | Exported functions, not a stable public API guarantee |
| Find bootstrap dependencies | `git grep -n -E 'InitVCL\|defaultBootstrap_InitialComponentContext' -- vcl4swt vcl/workben/minvcl.cxx` | Native initialization paths to read |
| Inspect target declarations | `git show HEAD:vcl4swt/Module_vcl4swt.mk` | What the module declares, not proof it is reachable in your configuration |
| Inspect linked libraries | `git show HEAD:vcl4swt/Library_vcl4swt.mk` | Why the experiment is not just one isolated source file |
| See a pending documentation diff | `git diff -- README.md docs` | Run in a checkout/branch that contains your documentation edits |
| Check accidental whitespace | `git diff --check` | Review output before proposing changes |

The `|` characters above are regular-expression alternation inside single quotes. In a Markdown table they are escaped for rendering; copy the rendered command, or use these plain examples:

```sh
git grep -n -E 'SAL_DLLPUBLIC_EXPORT|JNIEXPORT' -- vcl4swt/src/api
git grep -n -E 'InitVCL|defaultBootstrap_InitialComponentContext' -- vcl4swt vcl/workben/minvcl.cxx
```

## Compare snapshots in a shallow checkout

To inspect file differences without requiring the full ancestry:

```sh
git fetch --depth=1 origin master:refs/remotes/origin/master
git diff --stat origin/master HEAD
git diff origin/master HEAD -- vcl4swt VclUnoSwt autogen.input
```

These are two-endpoint comparisons. They are intentionally different from a three-dot merge-base comparison, which can fail when shallow history does not include the common ancestor. `origin/master` may now include later documentation; the pinned online [historical comparison](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/compare/ad8fa1b5912a04f4cc016965175315e4784fa229...19069d4d9992840913d2c085856a9af02420dc65) is the stable reference for the original experiment delta.

## Build boundary: read this before running configuration

The experiment inherits LibreOffice's native build system and dependencies. There is no verified one-command standalone VCL install or independent runtime package documented here.

1. Read the [inherited README](../../README.md) for this snapshot's toolchain assumptions.
2. Use LibreOffice's [platform build instructions](https://wiki.documentfoundation.org/Development/How_to_build) as setup guidance. Those pages evolve; reconcile them with this historical source instead of assuming the newest instructions match every old dependency.
3. Inspect `autogen.input` on the experiment branch. It enables debug utilities and the Office Development Kit; it is not a complete platform-specific dependency setup.
4. Inspect `Repository.mk`, `RepositoryModule_build.mk`, `RepositoryModule_host.mk`, and the experimental module before assuming a `vcl4swt` target builds in your configuration. The experiment history includes changes to target registration.
5. Only after platform prerequisites are satisfied, the inherited configure/build entry points are:

```sh
./autogen.sh
make
```

These commands configure and build inherited LibreOffice source, may fetch dependencies, and can consume substantial time, disk, and memory. They are not a validated standalone extraction recipe. Configure options, platform backends, and generated targets determine what actually builds.

The historical [Java example note](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/VclUnoSwt/readme.txt) says to build LibreOffice first, add the JAR dependencies from `instdir/program/classes` to the build path, and use `TextInMainControl.java`. It also records a position/size issue. There is no verified universal `java -jar`, Maven, or Gradle launcher to substitute for that setup.

## Test-source map and coverage boundary

Before selecting tests, identify whether you changed inherited VCL behavior, the experimental bridge, or the Java/UNO example. They have different entry points:

| Layer | Source to inspect | What it establishes |
| --- | --- | --- |
| Experimental native bridge | [Module targets](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/Module_vcl4swt.mk), [executable definition](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/Executable_test-vcl4swt.mk), and [demo main](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/src/test/test-vcl4swt.cxx) | The module declares `Library_vcl4swt` and `Executable_test-vcl4swt`; the executable opens the minimal-window path |
| Inherited VCL lifetime tests | [`CppunitTest_vcl_lifecycle.mk`](../../vcl/CppunitTest_vcl_lifecycle.mk) | CppUnit test setup with VCL/UNO libraries, components, and configuration dependencies |
| Inherited Skia tests | [`CppunitTest_vcl_skia.mk`](../../vcl/CppunitTest_vcl_skia.mk) and [`Module_vcl.mk`](../../vcl/Module_vcl.mk) | A non-headless VCL test target, registered when `SKIA` is in `BUILD_TYPE` |
| Java/UNO controls | [Historical example instructions](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/VclUnoSwt/readme.txt) | A manual example using a built LibreOffice tree, with a recorded position/size limitation |

This is a source map, not a claim that these targets run in every configuration. Follow the selected snapshot's build setup before attempting them. Inherited VCL tests do not certify the experimental SWT bridge or the later Initiative 31 custom-widget demonstrator.

For a runtime report, record the selected VCL backend and Skia settings. The inherited [environment-variable reference](../../vcl/README.vars.md) distinguishes `SAL_USE_VCLPLUGIN` from `SAL_ENABLESKIA` and the `SAL_SKIA` rendering-method selection. Enabling a variable alone does not prove the chosen backend supports or actually used that path. Avoid forcing a denylisted renderer merely to make an example start; diagnose and report the original behavior first.

## Verification checklist

- [ ] Record the exact branch and commit.
- [ ] Record OS, compiler/toolchain, Java version, configuration options, and relevant backend.
- [ ] Keep “configured,” “compiled,” “launched,” and “behavior checked” as separate results.
- [ ] Check window creation, event-loop behavior, disposal, and the actual widget you changed.
- [ ] Do not infer full SWT API compatibility from one example.
- [ ] Remove private paths, tokens, and unrelated machine details from shared logs.
- [ ] Review the changed file list; keep documentation changes separate from build/source changes.

The source links and command entry points were inspected during documentation authoring. Native compilation, GUI execution, and cross-platform behavior were not run or certified by this documentation change.
