# VCL extraction prototype: start here

[Root README](../../README.md) · [Command cheat sheet](CHEATSHEET.md) · [Examples and troubleshooting](EXAMPLES.md)

## What question was this experiment asking?

Could LibreOffice's existing widget layer help implement Eclipse SWT in a less OS-dependent way? Initiative 31 explored both direct access to LibreOffice's Visual Class Library (VCL) and use of UNO controls. This repository is the LibreOffice-side source experiment, with a large inherited office-suite tree around it.

The public [Skia/VCL assessment](https://github.com/swt-initiative31/documents/blob/main/results/skia_vcl.md) records partial examples and integration constraints. The [final project report](https://github.com/swt-initiative31/documents/blob/main/report/overall_report.md) describes the subsequent move to custom widgets with Skia. Do not mistake this earlier extraction experiment for that final demonstrator.

## Five concepts before you browse

| Concept | Meaning here |
| --- | --- |
| VCL | LibreOffice's Visual Class Library: widget/windowing code, OS abstraction, and rendering-related facilities |
| Skia | One rendering technology used by LibreOffice; a renderer is not a complete cross-platform widget implementation |
| UNO | LibreOffice's component model; an alternative investigated route to controls and services |
| JNI | A Java/native boundary explored by the experimental bridge |
| Extraction prototype | Research into using these pieces outside the complete product, not proof that they are already a self-contained supported toolkit |

The inherited [VCL README](../../vcl/README.md) also explains platform backends and distinguishes this library from Borland's unrelated Visual Component Library.

## The branch map matters

| Branch/snapshot | What is there | How to use it |
| --- | --- | --- |
| `master` at `ad8fa1b5912a04f4cc016965175315e4784fa229` | The inherited LibreOffice baseline | Read the VCL architecture and baseline build material |
| `vcl-4-swt` at `19069d4d9992840913d2c085856a9af02420dc65` | The experimental additions, including `vcl4swt/`, `VclUnoSwt/`, and `autogen.input` | Inspect the bridge, examples, and changes against the baseline |
| This documentation change | Fork-specific orientation and command/reference pages on the default branch | Use as a reading guide; it does not change either implementation |

The [public comparison](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/compare/ad8fa1b5912a04f4cc016965175315e4784fa229...19069d4d9992840913d2c085856a9af02420dc65) records 15 experimental commits ahead of the baseline. This count describes those pinned snapshots, not every future branch state.

The documentation is added on `master`; switching your checkout to the historical experiment can remove these newly added guide files from the working tree. Keep the guide open on GitHub or use separate checkouts while comparing branches.

## What the fork adds, and what it inherits

This fork adds a reader-facing introduction, practical source-inspection commands, a map of the experimental files, and troubleshooting guidance. It makes no new implementation, speed, compatibility, or production-readiness claim.

At the baseline check on 2026-10-14, the fork's `master` and its direct parent's `master` were identical at `ad8fa1b5912a04f4cc016965175315e4784fa229`. The extraction experiments are inherited from the Initiative 31 parent; they are not attributed here to this fork's owner. The parent repository was archived at that check.

Provenance chain:

1. [LibreOffice/core](https://github.com/LibreOffice/core): original source project and read-only GitHub mirror.
2. [swt-initiative31/prototype-skiavcl-libreoffice](https://github.com/swt-initiative31/prototype-skiavcl-libreoffice): Initiative 31's prototype fork.
3. [hsoliwal/initiative31-prototype-skiavcl-libreoffice](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice): this public fork and the added reader guides.

## Source map

### In the inherited baseline

| Path | Why it is useful |
| --- | --- |
| [vcl/README.md](../../vcl/README.md) | Responsibilities, platform abstractions, rendering, and further reading |
| [vcl/workben/minvcl.cxx](../../vcl/workben/minvcl.cxx) | Small VCL application: bootstrap, window, event loop, disposal |
| [vcl/Executable_vcldemo.mk](../../vcl/Executable_vcldemo.mk) | The demo's concrete build dependencies |
| [vcl/Module_vcl.mk](../../vcl/Module_vcl.mk) | Conditional platform targets, examples, and tests |
| [vcl/README.lifecycle.md](../../vcl/README.lifecycle.md) | Object lifetime and disposal context |
| [vcl/README.scheduler.md](../../vcl/README.scheduler.md) | Event scheduling context |
| [vcl/README.vars.md](../../vcl/README.vars.md) | Environment-variable reference; read before changing runtime behavior |
| [autogen.sh](../../autogen.sh) and [Makefile.in](../../Makefile.in) | The inherited configuration/build entry points |

### On the experiment snapshot only

All links below are pinned to `19069d4d9992840913d2c085856a9af02420dc65` so they remain meaningful from this default-branch guide.

| File | What to inspect |
| --- | --- |
| [vcl4swt/src/api/swtapi.cxx](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/src/api/swtapi.cxx) | Experimental exported window/button/calendar functions and a JNI entry point |
| [vcl4swt/Library_vcl4swt.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/Library_vcl4swt.mk) | Dependencies on VCL, UNO-related libraries, framework code, and external libraries |
| [vcl4swt/Module_vcl4swt.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/vcl4swt/Module_vcl4swt.mk) | Experimental module targets; target declarations alone do not establish a successful build |
| [VclUnoSwt/readme.txt](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/VclUnoSwt/readme.txt) | Historical Java example instructions and a stated position/size issue |
| [autogen.input](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/19069d4d9992840913d2c085856a9af02420dc65/autogen.input) | Experiment configuration: `--enable-dbgutil` and `--enable-odk` |

## Continue with a focused investigation

- For native lifetime or JNI questions, follow the [bridge-lifecycle reading exercise](EXAMPLES.md#example-4-review-lifetime-assumptions-before-calling-the-bridge)
- For test selection, use the [test-source map](CHEATSHEET.md#test-source-map-and-coverage-boundary) and distinguish the demo executable from assertion-based coverage
- For the SWT side of the earlier VCL experiment, start with [`swt-initiative31/prototype-skiavcl`](https://github.com/swt-initiative31/prototype-skiavcl) and the [Skia/VCL assessment](https://github.com/swt-initiative31/documents/blob/main/results/skia_vcl.md); do not assume this LibreOffice tree contains the Java SWT implementation
- For the later custom-widget demonstrator, follow [`prototype-skija`](https://github.com/swt-initiative31/prototype-skija) and its own setup/platform limitations

## Contributing and licensing

Keep a change narrowly scoped and state its target branch. A guide correction belongs on this fork's documentation branch; a claim about the prototype should identify the experiment revision and supporting public evidence. A source fix needs its own build and runtime verification.

The inherited [.gitreview](../../.gitreview) points to LibreOffice Gerrit, and the [Repo Lockdown workflow](../../.github/workflows/lockdown.yml) redirects upstream-style GitHub submissions. If enabled in this fork, that workflow can close newly opened PRs. A bot closure is not a technical review of the change; do not work around it by changing workflows as part of a documentation contribution.

The upstream [LibreOffice contribution guidance](https://wiki.documentfoundation.org/Development/GetInvolved) governs contributions to LibreOffice itself. This fork's documentation does not replace it or authorize submission to a different project.

Retain the original source headers and license material: [COPYING](../../COPYING), [COPYING.LGPL](../../COPYING.LGPL), and [COPYING.MPL](../../COPYING.MPL). A short repository summary is not a substitute for those texts or per-file notices.
