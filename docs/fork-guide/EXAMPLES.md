# Examples, reading exercises, and troubleshooting

[Start here](START_HERE.md) · [Cheat sheet](CHEATSHEET.md) · [Root](../../README.md)

## Example 1: understand the smallest inherited VCL window

Open [vcl/workben/minvcl.cxx](../../vcl/workben/minvcl.cxx) in the baseline. Follow these stages in the file:

1. Create a UNO component context and obtain/set the process service factory.
2. Configure the system language and initialize VCL.
3. Create a `WorkWindow`, set its title, and show it.
4. Enter the application's event loop with `Execute()`.
5. Dispose of the window, terminate the framework desktop, deinitialize VCL, and clear the service factory.

The useful lesson is the initialization/lifetime sequence and its dependencies. Copying just the window-creation expression is not a standalone application. Consult the [VCL lifecycle notes](../../vcl/README.lifecycle.md) and [scheduler notes](../../vcl/README.scheduler.md) before changing ownership or event behavior.

## Example 2: inspect what the extraction bridge actually exports

On the experiment branch, read [swtapi.cxx at the reviewed snapshot](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/src/api/swtapi.cxx).

```sh
git grep -n -E 'show_minvcl_window|add_button|add_calendar|JNIEXPORT' -- vcl4swt/src/api
git show HEAD:vcl4swt/Library_vcl4swt.mk
```

The file includes an exported minimal-window entry point, button/calendar experiments, and a JNI method that calls the minimal-window path. The library makefile links VCL, framework, and UNO-related libraries, among others. This is evidence of the experiment's shape, not of an independently packaged or stable API.

For a review note, record:

```text
Snapshot: <branch and commit>
Entry point inspected: <symbol>
Initialization assumptions: <what the source actually does>
Dependencies: <libraries/build targets from this revision>
Observed behavior: <only if you ran it, with environment>
Not established: <threading, lifetime, portability, or compatibility gaps>
```

## Example 3: locate the historical UNO example

Read [VclUnoSwt/readme.txt](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/VclUnoSwt/readme.txt) and then browse that snapshot's Java sources.

The note names `TextInMainControl.java`, expects a built LibreOffice tree, and points to JARs in `instdir/program/classes`. It warns about position and size behavior. Use it as a historical example to inspect and reproduce carefully, not as a tested launch recipe for arbitrary installed LibreOffice versions.

Compare your findings with the public [Skia/VCL assessment](https://github.com/swt-initiative31/documents/blob/main/results/skia_vcl.md), which separates VCL and UNO achievements and limitations. State which integration path you investigated.

## Example 4: review lifetime assumptions before calling the bridge

Read the bodies in [`swtapi.cxx`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/src/api/swtapi.cxx), not just their exported names:

- `show_minvcl_window()` creates the component context, installs the service factory, initializes VCL, runs the application, and then performs shutdown
- `TheApplication::Main()` assigns the shared `topWin`, calls `Execute()`, and disposes its window after the event loop exits
- `add_button()` and `add_calendar()` use that shared window and explicitly acquire the VCL yield mutex
- The function named `deinit()` does **not** mirror the shutdown in `show_minvcl_window()` at this snapshot: its body creates a context and calls `InitVCL()`

These source observations are a reason to review call order, thread ownership, and disposal before building a caller. They do not establish a supported `init()`/`deinit()` lifecycle or safe arbitrary calls from Java threads. This guide records the behavior found in the historical source; it does not fix or execute it.

A useful investigation separates three questions: which function owns the event loop, when the window pointer is valid, and which path releases VCL/UNO resources. Compare the answers with the inherited [lifecycle notes](../../vcl/README.lifecycle.md) and [scheduler notes](../../vcl/README.scheduler.md). Record an expected sequence and reproduce it explicitly before claiming the bridge can be reused.

## Example 5: distinguish a demo executable from test coverage

The experimental [`Executable_test-vcl4swt.mk`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/Executable_test-vcl4swt.mk) defines an executable linked against `vcl4swt`, VCL, and UNO-related libraries. Its [`test-vcl4swt.cxx`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/src/test/test-vcl4swt.cxx) calls `show_minvcl_window()` and returns zero afterward; it does not contain assertions covering SWT behavior.

Therefore:

1. A declared executable is evidence of an intended demonstration entry point
2. A successful build, if reproduced, establishes compilation/linking for that configuration
3. An opened window establishes only that observed path in that environment
4. Layout, events, focus, resizing, disposal, and cross-platform behavior each require explicit checks

For inherited automated-test entry points and configuration caveats, use the [test-source map](CHEATSHEET.md#test-source-map-and-coverage-boundary). A filename containing `test` is not a compatibility test suite.

## Troubleshooting by symptom

| Symptom | Likely distinction to check | Next step |
| --- | --- | --- |
| `vcl4swt/` or `VclUnoSwt/` is missing | You may be on `master` | Check `git branch --show-current`; inspect the experiment branch or its pinned links |
| The added guides vanish after switching branches | They were added on the default documentation branch | Keep the guide open online or use separate checkouts |
| Three-dot Git comparison cannot find a merge base | A shallow clone may lack ancestry | Use the two-endpoint comparison in the cheat sheet or deliberately fetch the needed history |
| Configuration fails immediately | Missing or mismatched historical toolchain/dependencies | Read the first configure error and compare platform setup with the snapshot; do not assume an extraction-specific bug |
| A declared experimental target is unavailable | Module registration and configuration affect reachable targets | Inspect repository/module makefiles at the same revision; report the exact target and configuration |
| Java cannot resolve UNO classes | The historical example expects JARs from a built tree | Recheck its readme and the build path; do not invent a standalone JAR launcher |
| A window appears but behavior is wrong | Window creation alone does not validate events, layout, or widget semantics | Record the specific example, revision, backend, and expected/actual behavior |
| A new GitHub PR closes automatically | The inherited Repo Lockdown workflow may be enabled | Inspect the PR's bot comment/actions and preserve the branch; this guide does not change repository policy |

## Reporting a result usefully

Include a commit-pinned source link, branch, build configuration, environment, exact command or example, expected result, actual result, and the smallest relevant log excerpt. Distinguish a build failure from a launch failure or behavioral mismatch. Never include credentials or private source material.

A documentation PR should state which links and source claims were checked. A runtime claim requires its own reproducible test evidence. The documentation in this directory was source-reviewed; it does not claim a successful native build or GUI test.
