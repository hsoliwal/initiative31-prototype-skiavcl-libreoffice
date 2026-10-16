# Documentation coverage and verification boundary

[Start here](START_HERE.md) · [Build and root index](MODULE_INDEX.md) · [Module manifests](MODULE_MANIFESTS.md) · [Prototype contracts](PROTOTYPE_CONTRACTS.md) · [VCL/Skia contracts](VCL_SKIA_CONTRACTS.md)

## Scope and provenance

The source project is [LibreOffice/core](https://github.com/LibreOffice/core).
The Initiative 31 experiment comes through
[`swt-initiative31/prototype-skiavcl-libreoffice`](https://github.com/swt-initiative31/prototype-skiavcl-libreoffice).
This documentation is for the public
[`hsoliwal/initiative31-prototype-skiavcl-libreoffice`](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice)
fork. It attributes inherited code and experimental work to those source
projects; it does not claim that this fork authored or newly implemented them.

| Snapshot | Role in this review | Inventory boundary |
| --- | --- | --- |
| `38f3847c224e4d735a199e596b11b0a1cf9488e5` | Fork `master` baseline for this documentation expansion | Complete superproject tree, excluding descendants of gitlinks and downloaded archives |
| `19069d4d9992840913d2c085856a9af02420dc65` | Historical `vcl-4-swt` extraction experiment | Complete root list and complete `vcl4swt` / `VclUnoSwt` subtrees; selected registration files and bodies |
| `ad8fa1b5912a04f4cc016965175315e4784fa229` | Earlier baseline used by the existing historical guide/comparison | Retained historical context; not substituted for the baseline inventoried here |

The expanded reference is Markdown-only. It does not change public APIs, source
comments, build scripts, workflows, disabled paths, licenses, dependency
versions, or experimental behavior. Existing upstream guides and notices are
retained. In particular,
[COPYING](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/COPYING),
[COPYING.LGPL](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/COPYING.LGPL),
[COPYING.MPL](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/COPYING.MPL),
and file-level notices remain the sources to consult. This documentation is not
a legal compatibility assessment.

## Inventory completion is not semantic completion

The complete baseline inventory was reconstructed from the root tree and
non-truncated subtree responses. Large whole-tree and `icon-themes` recursive
reads did not produce usable results; the successful inventory used all 150
root directory trees, with `icon-themes` split into its 20 child theme trees.
Each final component tree was non-truncated, and combined paths were checked
for duplicates. The 3 gitlinks were retained as boundaries.

| Measure | Observed count | What it does not establish |
| --- | ---: | --- |
| Baseline tracked entries | 155,737 | Package/API semantics |
| Baseline blobs | 146,657 | Source files only; this also includes assets and fixtures |
| Baseline directory trees | 9,077 | 9,077 language packages or modules |
| Baseline gitlinks | 3 | Reviewed contents of those separate repositories |
| `Module_*.mk` candidate paths | 230 | Configured or substantively documented modules |
| Candidate module bodies reviewed | 2 | Complete semantics of VCL or the external Skia dependency |
| Remaining candidate module bodies | 228 | Exclusions from scope; these remain open |
| Baseline `.mk` paths | 2,485 | Active targets or independent projects |
| Baseline `.java` / `.idl` paths | 2,574 / 5,519 | Extracted package declarations or documented API counts |
| Experimental `vcl4swt` files | 10 | Successful compilation or a stable supported API |
| Experimental `VclUnoSwt` files | 22, including 20 Java files | All Java class/package semantics reviewed |

Every root directory and every candidate module-definition path is listed in
the [root index](MODULE_INDEX.md#root-directory-inventory) and
[manifest inventory](MODULE_MANIFESTS.md). “Unreviewed” means substantive
documentation is still missing; the index does not reclassify it as complete.
There is no claimed percentage of fully documented packages because the complete
language namespace denominator has not yet been established.

## Reviewed semantic scope

| Area | Source evidence examined | Documentation outcome |
| --- | --- | --- |
| Repository build boundary | `Makefile.gbuild`, both `RepositoryModule_*.mk` files, `Repository.mk`, selected `solenv/gbuild/Module.mk` machinery | Aggregate/target/configuration distinctions; not a configured graph |
| Inherited VCL | `vcl/Module_vcl.mk`, `vcl/Library_vcl.mk`, VCL guides, complete `minvcl.cxx` and `include/vcl/vclptr.hxx` bodies | Selected application sequence, reference/disposal contracts, backend selection boundaries |
| Inherited Skia helpers | Public helper header, complete `SkiaHelper.cxx`, internal utility/zone declarations and `zone.cxx` | Stateful enablement, method/fallback choices, selected resource/failure/diagnostic effects |
| External Skia integration | `external/skia/Module_skia.mk`, `UnpackedTarball_skia.mk`, README and tarball-list context | Downloaded-source/patch boundary; not every patch or external library API |
| Test evidence | Lifecycle and Skia target definitions; lifecycle bodies; Skia registrations, all enablement guards and selected assertion bodies | Existing coverage intentions and skip conditions; no executed-test result |
| Native experiment | Experimental repository registrations, module/library/executable definitions, both API headers, complete bridge and both demonstration bodies | All eight declared C entry points, JNI boundary, shared state and lifecycle gaps |
| Java experiment | `.classpath`, readme, complete `TextInMainControl`, `MinVclBootstrap`, `MinVclStart`, `ExecuteOfficePipe` bodies | Selected `main`, `start`, and `pipetest` namespace contracts; remaining class declarations/bodies unreviewed |

Each substantive page links to the exact source files at its stated revision.
“Implemented” observations describe a body present in the source; they do not
mean it is correct, tested, supported, thread-safe, or portable. Existing README
guidance is distinguished from source implementation when they differ.

## Explicit open boundaries

1. The `dictionaries`, `helpcontent2`, and `translations` gitlinks remain
   unexpanded. Their pinned commits and recorded relative URLs are in the
   [submodule table](MODULE_INDEX.md#separate-submodule-repositories).
2. Downloaded third-party archives, generated build outputs, generated API
   artifacts not tracked in Git, and external dependency transitive sources
   are not part of the completed superproject tree inventory. Their own
   namespaces, modules, licenses, and contracts remain unreviewed.
3. All 228 candidate module definitions marked unreviewed, all remaining
   target definitions, all alternate build/module paths listed in the index,
   and all root directory semantics beyond the selected references remain
   open. Tracking their names does not satisfy their substantive documentation.
4. Baseline Java, UNO IDL, C++, Python, C#, JavaScript, SDK/example, test-only,
   generated-interface, and other language package boundaries have not been
   exhaustively extracted or reviewed. The folder and extension counts are not
   substitutes for declaration evidence.
5. VCL widget/public-header APIs, scheduler implementation, platform backends,
   and most bitmap/graphics rendering bodies remain unreviewed. The selected
   ownership/helper contracts do not certify the rest of VCL.
6. In `VclUnoSwt`, 16 of the 20 Java bodies remain unreviewed: the 13 `src/main`
   classes and three context/exception classes named in the
   [prototype reference](PROTOTYPE_CONTRACTS.md). Their exact tracked paths are
   known, but their package declarations and leaf API semantics are not claimed
   verified.
7. The full experiment snapshot outside its root and two focused subtrees was
   not independently expanded. Baseline inventory counts do not describe that
   entire revision, and selected registration reads do not enumerate every
   experimental change.
8. Inline documentation is unchanged. Misleading lifecycle/parameter comments
   and missing ownership/error/thread contracts are recorded in Markdown;
   this pass does not claim every inline contract is now repaired.

No unresolved boundary above is a silent exclusion. Each needs a later
source-backed pass, with its actual project/module/package vocabulary and
test/verification evidence, before an all-repository documentation claim could
be made.

## Verification and non-results

This editorial pass retrieves public metadata/source and performs local text,
inventory, link-target, heading-fragment, count, scope, and content-integrity
checks. These checks do not execute repository code or the commands shown in
the existing guides. The PR's publication report records the final changed-file
and remote-content checks for the published commit.

| Stage | Result boundary |
| --- | --- |
| Tree/path inventory | Complete for the pinned baseline superproject; explicit gitlink/archive limits above |
| Source/manifest examination | Selected scope listed above; most semantic boundaries remain open |
| Documentation text checks | Only documentation structure, source/path references, counts, and permitted file scope are checked |
| Repository linter / build configuration | Not run |
| Native compilation / Java compilation | Not run |
| CppUnit / other automated tests | Not run |
| GUI / GPU / platform / SWT behavior | Not run |
| Merge / deployment / workflow changes | Not performed |

## M3 interpretation boundary

The inventory and explicit contract/gap records can inform a proposed M3
documentation workflow. They do not establish an implemented M3 agent kernel,
IR, recognizer, deterministic promotion system, proof receipt mechanism,
checkpoint/restart guarantee, or semantic fixed point in this repository.
Matching source hashes is an integrity/freshness check, not a semantic proof.
No private design essays, transcripts, or unrelated repository information are
included in these public pages.
