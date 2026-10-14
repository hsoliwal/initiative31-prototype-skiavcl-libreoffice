# Experimental bridge and Java/UNO contracts

[Start here](START_HERE.md) · [Build and module boundaries](MODULE_INDEX.md) · [VCL and Skia](VCL_SKIA_CONTRACTS.md) · [Coverage](COVERAGE.md)

## Revision and status

This page describes the historical `vcl-4-swt` snapshot
`19069d4d9992840913d2c085856a9af02420dc65`. It does not describe code added by this
documentation PR or code present in the current `master` baseline. The native
bridge and Java examples are inherited Initiative 31 experiments. Source
observations below are not successful build, runtime, SWT-compatibility, or
production-readiness results.

The complete tracked subtrees contain 15 entries under `vcl4swt/` (10 files and
5 directories) and 26 under `VclUnoSwt/` (22 files and 4 directories). The latter
contains 20 Java source files, not a Maven or Gradle project. Neither subtree
contains an `AGENTS.md`, `CLAUDE.md`, or Java `module-info.java`.

## Native gbuild project: vcl4swt

The [module definition](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/Module_vcl4swt.mk)
registers `Library_vcl4swt` and `Executable_test-vcl4swt` in its active target
list. It also contains commented experimental material; comments do not add
targets. The [host repository manifest](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/RepositoryModule_host.mk)
lists `vcl4swt`. The [build-side manifest](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/RepositoryModule_build.mk)
lists it inside the `WITH_GALLERY_BUILD` group. These are configuration-dependent
registration facts, not proof that an arbitrary checkout has a usable target.

The [library definition](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/Library_vcl4swt.mk)
compiles the single `vcl4swt/src/api/swtapi` exception object and exposes both
`vcl4swt/inc` and the inherited private `vcl/inc` headers to it. It uses the SDK
API and links `tl`, `sal`, `vcl`, `cppu`, `cppuhelper`, `comphelper`,
`i18nlangtag`, and `fwk`. Its external list includes Boost headers, Expat,
Frozen, GIO, Graphite, HarfBuzz, ICU, Little CMS, libeot, JPEG, PNG, TIFF, and
WebP integrations. This dependency graph explains why the bridge is not a
standalone window library simply because it has one implementation file.

The experimental [repository target registry](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/Repository.mk)
contains `test-vcl4swt` and `vcl4swt` entries. It still has a nearby TODO about
adding the library, although the library entry is present. Read the actual lists
rather than treating that comment as definitive registration status.

### C and JNI surface

The C-linkage [header](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/inc/api/swtapi.hxx)
declares eight no-argument functions returning `int`. All eight bodies in
[`swtapi.cxx`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/src/api/swtapi.cxx)
return zero on their normal path. There is no documented result-code taxonomy,
per-call handle, or exception-to-error-code conversion in this implementation.
The absence of such handling is a contract gap, not a promise that calls cannot
fail.

| Function | Implemented effect | Caller-visible constraint or gap |
| --- | --- | --- |
| `show_minvcl_window()` | Constructs `TheApplication`, bootstraps the UNO context/service factory, sets the system language, calls `InitVCL()`, runs `Main()`, then terminates the framework desktop, calls `DeInitVCL()`, and clears the service factory | This call owns a synchronous event-loop path. It does not immediately return a window handle. Early failures and reentrant use are not wrapped in a cleanup/error protocol |
| `init()` | Constructs a local `TheApplication`, bootstraps UNO, installs the process service factory, sets the system language, and calls `InitVCL()` | The local application object is not retained as an explicit session object. It does not run `Main()` or initialize `topWin` |
| `deinit()` | Repeats the context/service-factory/language initialization and calls `InitVCL()` | Despite its name, it does not call `DeInitVCL()` or mirror the shutdown in `show_minvcl_window()` |
| `show_window()` | Assigns a new `WorkWindow` to global `win`, sets a fixed title, and shows it | Assumes initialized VCL; this is a different global from `topWin`. No event loop is started here |
| `close_window()` | Calls `win.disposeAndClear()` | It targets `win`, not the window stored in `topWin`. No matching application shutdown occurs here |
| `set_text()` | Sets a fixed title through global `topWin` | No null/disposal guard, text parameter, or explicit yield-mutex acquisition appears in this body |
| `add_button()` | Acquires the VCL yield mutex, creates a `PushButton` parented by `topWin`, assigns fixed text and geometry, shows it, then releases the mutex | Uses a shared global `button`; acquisition/release is manual and no exception-safe guard or caller-controlled geometry is provided |
| `add_calendar()` | Acquires the same mutex, creates a `CalendarField` parented by `topWin`, assigns fixed geometry, shows it, and releases the mutex | Uses shared global `calendar`; the same call-order, ownership, and manual-locking questions apply |

`TheApplication::Main()` creates and shows its member `mpWin`, assigns it to
`topWin`, calls `Execute()`, and disposes `mpWin` after the loop returns. It does
not explicitly clear the separate global `topWin` reference. The declarations
and bodies therefore do not establish a reusable independent `init()` /
`show_window()` / `close_window()` / `deinit()` session protocol. Do not present
that sequence as a validated usage example.

The machine-generated [JNI header](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/inc/api/app_App.h)
declares `Java_app_App_showMinVCLWindowUsingJNI(JNIEnv*, jobject)` with Java
signature `()V`. Its implementation ignores both parameters and calls
`show_minvcl_window()`. It does not add dispatch to a GUI thread, cancellation,
native-handle ownership, or Java exception translation. The two inventoried
experiment subtrees contain no `app/App.java`; a generated JNI name is not
evidence of a complete Java caller in these directories.

### Demonstrations and unregistered work

- [`test-vcl4swt.cxx`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/src/test/test-vcl4swt.cxx)
  calls `show_minvcl_window()` and returns zero. Its
  [executable definition](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/Executable_test-vcl4swt.mk)
  links the bridge plus inherited VCL/UNO/framework libraries. The executable
  contains no assertion suite or SWT parity checks.
- [`windowbutton.cxx`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/src/test/windowbutton.cxx)
  has a separate bootstrap/main path, a `WorkWindow` subclass, a child button,
  `Application::Execute()`, a `Close()` override that can call
  `Application::Quit()`, and explicit child disposal before base disposal.
  [`Executable_windowbutton.mk`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/Executable_windowbutton.mk)
  exists, but `Module_vcl4swt.mk` does not register it in the active target list.
  Its buildability and runtime behavior remain unverified; do not silently add
  or activate it as part of documentation work.

## Java example project: VclUnoSwt

The complete tree has an Eclipse-style [`.classpath`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/VclUnoSwt/.classpath),
with `src` as its source directory, `bin` as output, a JavaSE-17 JRE container,
and many absolute development-machine paths to LibreOffice JARs. Those paths
are historical configuration, not a portable setup recipe. The
[readme](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/VclUnoSwt/readme.txt)
requires a built LibreOffice tree, the JARs under `instdir/program/classes`, and
identifies `TextInMainControl.java` as the example. It records a position/size
issue. No Maven POM, Gradle build, `.project`, or Java module descriptor is
tracked in this subtree.

### Namespace main: selected UNO control example

[`main.TextInMainControl`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/VclUnoSwt/src/main/TextInMainControl.java)
calls `start.MinVclBootstrap.bootstrap()`, obtains the UNO Toolkit and Desktop,
and uses the current desktop frame's container window as the host. It constructs
a `UnoControlFixedTextModel`, sets properties, assigns the model to a
`UnoControlFixedText`, creates a peer, and explicitly resets the peer position
and size. It changes backgrounds and invalidates regions as part of the
experiment. The full body has been inspected; it is not a minimal general API.

Its `qi(Class<T>, Object)` helper delegates to `UnoRuntime.queryInterface`.
`main(String[])` assumes that the component context, current frame, queried
interfaces, and peers are usable at several points without null checks. Its
catch block prints an exception and stack trace; `System.exit(0)` follows even
after that catch. A zero process exit is therefore not evidence that the GUI
path succeeded. The body does not provide a structured shutdown of the office
process or a general disposal contract for every created UNO object.

The other 13 `src/main` classes remain path-inventoried, with their bodies and
public contracts unreviewed in this pass: `DialogDocument`, `DisplayAndButton`,
`DisplayButtonInMain`, `FirstLoadComponent`, `FirstUnoContact`,
`ImageControlSample`, `MessageBox`, `RoadmapItemStateChangeListener`,
`SystemDialog`, `UnoDialogSample`, `UnoDialogSample2`, `UnoMenu`, and `UnoMenu2`.
Their filenames alone are not substantive API documentation or proof that all
declare the same Java package. The `main` declaration is verified in the
selected `TextInMainControl` body.

### Namespace start: bootstrap and process boundary

[`start.MinVclBootstrap`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/VclUnoSwt/src/start/MinVclBootstrap.java)
contains Java-side service-manager/bootstrap support adapted from inherited
LibreOffice material. Preserve its MPL/Apache notices when examining or reusing
it; the directory name does not establish original authorship.

| API | Inputs and output | Effects, errors, and limits in the inspected body |
| --- | --- | --- |
| `getDefaultOptions()` | Returns four command-line strings | The array contains `--nologo`, `--nodefault`, `--norestore`, and `--nolockcheck`; returning it does not establish that the launcher applies it |
| `createInitialComponentContext(Map<String,Object>)` and compatibility `Hashtable` overload | Accepts context entries or null; returns `XComponentContext` | Creates a `ServiceManager`, loader, and `ComponentContext`, writes the service-manager singleton into the supplied map when non-null, and registers the basic factories; declares `Exception` |
| `createSimpleServiceManager()` | Returns `XMultiServiceFactory` | Builds the initial context and queries its service manager; declares `Exception` |
| `defaultBootstrap_InitialComponentContext(...)` overloads | Optional initialization file and bootstrap parameter map; returns a queried `XComponentContext` | Converts the map to pairs, conditionally loads native `juh` support, and calls the private native `cppuhelper_bootstrap`. Android has a separate `lo-bootstrap` loading branch; this path is not the same as the process-spawning `bootstrap` below |
| `bootstrap()` / `bootstrap(String[])` | Returns the remote `XComponentContext`; declares `BootstrapException` | Locates `soffice`/`soffice.exe` through the class loader, launches it with a random UNO pipe acceptance argument, forwards stdout/stderr with threads, and resolves the remote context |
| `bootstrapWebsocketConnection(String)` | Server URL to a remote `XComponentContext` | Resolves a UNO WebSocket connection using a local resolver; this body does not launch `soffice` or use the pipe retry loop |

Important implementation-specific limits:

1. `bootstrap(String[])` allocates a command array of length two. The statement
   that would copy `argArray` into it is commented out. Consequently the
   supplied options, including those returned by `getDefaultOptions()`, are not
   forwarded by this historical body. Do not repeat the inherited parameter
   Javadoc as a verified description of the modified implementation.
2. The pipe connection retries `NoConnectException` after 500 ms sleeps and
   throws when the counter reaches 600. This bounds that retry/sleep sequence;
   it is not a wall-clock guarantee for arbitrary blocking process or resolver
   operations.
3. `BootstrapException` and Java runtime exceptions are rethrown; other checked
   exceptions are wrapped. The launched `Process` is local to the method and
   the body does not destroy it on connection failure or expose a shutdown
   handle to the caller.
4. The native bootstrap loading flag and service/context objects are not a
   demonstrated thread-safe session manager. Thread-safety, native symbol
   availability, retries after failure, and complete cleanup have not been
   verified.

[`start.MinVclStart`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/VclUnoSwt/src/start/MinVclStart.java)
is another manual launcher: it bootstraps, creates a Toolkit service, prints
periodically for approximately 100 seconds, and catches exceptions for output.
It provides no assertion-based success criterion. `BootstrapException`,
`ComponentContext`, and `ComponentContextEntry` are also tracked in `src/start`;
their complete bodies and declarations remain unreviewed here.

### Namespace pipetest: native process experiment

[`pipetest.ExecuteOfficePipe`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/VclUnoSwt/src/pipetest/ExecuteOfficePipe.java)
has one source file in its directory. It constructs a random UNO pipe argument
and starts a hard-coded native `minvcl` executable through
`Runtime.getRuntime().exec`. It creates a `ProcessBuilder` and configures its
directory, but does not use that builder to start the process. Therefore the
builder's directory is not applied to the actual launch. The default options
are read but not added to the command. Separate threads forward child output;
the main thread sleeps while the child is alive. The body does not impose a
timeout, validate a UNO connection, or interpret an exit code as a test result.

The hard-coded path and printed environment make this an inspect-before-running
development experiment. Avoid publishing environment dumps in a reproduction
report. Do not replace the historical path with a guessed local path and call
that a verified setup procedure.

## Review and reproduction obligations

Before treating either integration path as reusable, establish the intended
caller and owning GUI thread, the process/application lifetime, valid window
states, disposal order, failure propagation, and actual dependencies for the
chosen platform. A source-level call graph alone does not settle those issues.
Record build, launch, widget behavior, and cleanup separately. Neither the
native demonstration nor the Java example is a certification of SWT API parity.

This page adds Markdown explanations only. It does not repair the misleading
`deinit` name/body, bootstrap parameter documentation, hard-coded configuration,
missing cleanup contracts, or unregistered target. Those remain visible source
and documentation gaps for separately authorized, verified work.
