# Build and repository boundary index

[Start here](START_HERE.md) · [Module manifest inventory](MODULE_MANIFESTS.md) · [Experimental contracts](PROTOTYPE_CONTRACTS.md) · [VCL/Skia contracts](VCL_SKIA_CONTRACTS.md) · [Coverage](COVERAGE.md)

## What this index measures

Baseline: `38f3847c224e4d735a199e596b11b0a1cf9488e5` on the public fork's `master`.
The complete superproject inventory contains 155,737 tracked entries: 146,657
blobs, 9,077 directory trees, and 3 gitlinks. All 150 root directory trees were
expanded; this excludes the contents of the three separate submodule repositories
and build-time downloads. It includes assets, fixtures, tests, examples, tooling,
and inherited/vendor-related paths. It is not a count of APIs or documented
packages.

A directory is not automatically a package. This repository primarily uses
LibreOffice gbuild modules and target definitions. C++ namespaces and UNO/Java
packages can span directories; gbuild `Package_*` files describe build packaging,
not necessarily language namespaces. The inventory below records exact paths and
unreviewed boundaries rather than inventing a universal repository/project/module/
package hierarchy.

## How the build boundaries fit together

- [Makefile.gbuild](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/Makefile.gbuild) defaults `gb_Side` to `host`, reads `config_$(gb_Side).mk`, loads gbuild, and passes `RepositoryModule_$(gb_Side).mk` to the global module-target machinery
- [RepositoryModule_host.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/RepositoryModule_host.mk) defines the `libreoffice` aggregate and lists host-side module directories, including conditional feature/platform groups
- [RepositoryModule_build.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/RepositoryModule_build.mk) defines the `cross_toolset` aggregate and a different build-side module set, including a `WITH_GALLERY_BUILD` group
- [solenv/gbuild/Module.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/solenv/gbuild/Module.mk) records module identity/location and connects target groups and submodules; a target filename alone does not evaluate these conditions
- [Repository.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/Repository.mk) contains central target registration; the module makefiles select targets, and `Library_*`, `Executable_*`, test and other definitions supply their details
- The configuration entry points are [autogen.sh](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/autogen.sh) and [configure.ac](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/configure.ac); these paths were inventoried, not fully audited or executed in this pass

The active graph depends on generated configuration. No configuration was
evaluated, so there is no claimed universal list of active targets or supported
platform/toolchain matrix. Follow the existing [build boundary](CHEATSHEET.md#build-boundary-read-this-before-running-configuration)
for historical setup context. Do not substitute a gbuild filename list for a
successful configuration/build.

## Substantive reference coverage

| Boundary | Current explanation | Remaining work |
| --- | --- | --- |
| Repository and build aggregates | Provenance, configuration/registration distinction, complete superproject path inventory | Full configured dependency graph and operational verification |
| Inherited VCL / selected shared headers | [Lifetime, ownership, Skia selection and test contracts](VCL_SKIA_CONTRACTS.md) | Most APIs and platform/backend bodies remain unreviewed |
| `external/skia` | Tarball/patch boundary and selected module registration | Archive contents, patch semantics, complete library build and licensing review |
| Experimental `vcl4swt` | [All eight declared C entry points, JNI entry point, registered demo and unregistered executable](PROTOTYPE_CONTRACTS.md#native-gbuild-project-vcl4swt) | Runtime lifecycle, failures, thread ownership, packaging and compatibility verification |
| Experimental `VclUnoSwt` | [Three declaration-evidenced namespaces and selected complete implementation bodies](PROTOTYPE_CONTRACTS.md#java-example-project-vclunoswt) | Remaining class declarations/bodies and API contracts, portable setup and cleanup verification |
| All other inherited boundaries | Path inventory and candidate build-definition links below | Substantive package/API/module semantics remain open |

The experiment is a second pinned snapshot, `19069d4d9992840913d2c085856a9af02420dc65`.
Its complete root was listed, and both experiment directories were expanded.
Its entire inherited tree was not independently expanded; the baseline's complete
inventory must not be relabeled as a complete experiment inventory.

## Root directory inventory

Each row covers the named baseline directory and every tracked descendant in
that superproject subtree. Counts are files/blobs and `Module_*.mk` candidate
paths, not configured modules. “Selected” means the linked reference reviews
only selected contracts; it never means the entire row is complete. Every
“Unreviewed” row remains in the semantic documentation backlog.

| Root boundary | Blobs | Module-definition candidates | Semantic coverage |
| --- | ---: | ---: | --- |
| [.git-hooks/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/.git-hooks) | 4 | 0 | Unreviewed; inventory only |
| [.github/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/.github) | 2 | 0 | Unreviewed; inventory only |
| [.vscode/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/.vscode) | 2 | 0 | Unreviewed; inventory only |
| [UnoControls/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/UnoControls) | 24 | 1 | Unreviewed; inventory only |
| [accessibility/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/accessibility) | 147 | 1 | Unreviewed; inventory only |
| [android/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/android) | 273 | 1 | Unreviewed; inventory only |
| [animations/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/animations) | 7 | 1 | Unreviewed; inventory only |
| [apple_remote/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/apple_remote) | 18 | 1 | Unreviewed; inventory only |
| [avmedia/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/avmedia) | 75 | 1 | Unreviewed; inventory only |
| [basctl/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/basctl) | 151 | 1 | Unreviewed; inventory only |
| [basegfx/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/basegfx) | 89 | 1 | Unreviewed; inventory only |
| [basic/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/basic) | 411 | 1 | Unreviewed; inventory only |
| [bean/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/bean) | 39 | 1 | Unreviewed; inventory only |
| [bin/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/bin) | 109 | 0 | Unreviewed; inventory only |
| [binaryurp/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/binaryurp) | 40 | 1 | Unreviewed; inventory only |
| [bridges/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/bridges) | 182 | 1 | Unreviewed; inventory only |
| [canvas/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/canvas) | 224 | 1 | Unreviewed; inventory only |
| [chart2/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/chart2) | 1,225 | 1 | Unreviewed; inventory only |
| [cli_ure/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/cli_ure) | 59 | 1 | Unreviewed; inventory only |
| [codemaker/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/codemaker) | 40 | 1 | Unreviewed; inventory only |
| [comphelper/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/comphelper) | 146 | 1 | Unreviewed; inventory only |
| [compilerplugins/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/compilerplugins) | 433 | 0 | Unreviewed; inventory only |
| [config_host/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/config_host) | 48 | 0 | Unreviewed; inventory only |
| [configmgr/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/configmgr) | 77 | 1 | Unreviewed; inventory only |
| [connectivity/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/connectivity) | 802 | 1 | Unreviewed; inventory only |
| [cppcanvas/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/cppcanvas) | 57 | 1 | Unreviewed; inventory only |
| [cppu/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/cppu) | 70 | 1 | Unreviewed; inventory only |
| [cppuhelper/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/cppuhelper) | 62 | 1 | Unreviewed; inventory only |
| [cpputools/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/cpputools) | 10 | 1 | Unreviewed; inventory only |
| [cui/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/cui) | 518 | 1 | Unreviewed; inventory only |
| [dbaccess/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/dbaccess) | 812 | 1 | Unreviewed; inventory only |
| [desktop/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/desktop) | 697 | 1 | Unreviewed; inventory only |
| [distro-configs/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/distro-configs) | 53 | 0 | Unreviewed; inventory only |
| [docmodel/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/docmodel) | 12 | 1 | Unreviewed; inventory only |
| [docs/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/docs) | 3 | 0 | Existing guides and this reference; no runtime component |
| [drawinglayer/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/drawinglayer) | 206 | 1 | Unreviewed; inventory only |
| [editeng/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/editeng) | 156 | 1 | Unreviewed; inventory only |
| [embeddedobj/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/embeddedobj) | 94 | 1 | Unreviewed; inventory only |
| [embedserv/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/embedserv) | 35 | 1 | Unreviewed; inventory only |
| [emfio/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/emfio) | 81 | 1 | Unreviewed; inventory only |
| [eventattacher/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/eventattacher) | 7 | 1 | Unreviewed; inventory only |
| [extensions/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/extensions) | 534 | 1 | Unreviewed; inventory only |
| [external/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/external) | 1,327 | 95 | Selected external/skia integration; other dependency bodies unreviewed |
| [extras/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/extras) | 5,051 | 1 | Unreviewed; inventory only |
| [filter/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/filter) | 758 | 1 | Unreviewed; inventory only |
| [forms/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/forms) | 262 | 1 | Unreviewed; inventory only |
| [formula/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/formula) | 36 | 1 | Unreviewed; inventory only |
| [fpicker/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/fpicker) | 93 | 1 | Unreviewed; inventory only |
| [framework/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/framework) | 392 | 1 | Unreviewed; inventory only |
| [helpcompiler/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/helpcompiler) | 18 | 1 | Unreviewed; inventory only |
| [hwpfilter/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/hwpfilter) | 70 | 1 | Unreviewed; inventory only |
| [i18nlangtag/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/i18nlangtag) | 18 | 1 | Unreviewed; inventory only |
| [i18npool/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/i18npool) | 493 | 1 | Unreviewed; inventory only |
| [i18nutil/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/i18nutil) | 14 | 1 | Unreviewed; inventory only |
| [icon-themes/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/icon-themes) | 89,921 | 0 | Unreviewed; inventory only |
| [idl/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/idl) | 30 | 1 | Unreviewed; inventory only |
| [idlc/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/idlc) | 11 | 0 | Unreviewed; inventory only |
| [include/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/include) | 2,597 | 0 | Selected VclPtr and SkiaHelper declarations; other headers unreviewed |
| [instsetoo_native/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/instsetoo_native) | 134 | 1 | Unreviewed; inventory only |
| [io/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/io) | 36 | 1 | Unreviewed; inventory only |
| [ios/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/ios) | 16 | 1 | Unreviewed; inventory only |
| [javaunohelper/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/javaunohelper) | 30 | 1 | Unreviewed; inventory only |
| [jurt/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/jurt) | 13 | 1 | Unreviewed; inventory only |
| [jvmaccess/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/jvmaccess) | 16 | 1 | Unreviewed; inventory only |
| [jvmfwk/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/jvmfwk) | 51 | 1 | Unreviewed; inventory only |
| [l10ntools/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/l10ntools) | 52 | 1 | Unreviewed; inventory only |
| [librelogo/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/librelogo) | 9 | 1 | Unreviewed; inventory only |
| [libreofficekit/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/libreofficekit) | 48 | 1 | Unreviewed; inventory only |
| [lingucomponent/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/lingucomponent) | 43 | 1 | Unreviewed; inventory only |
| [linguistic/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/linguistic) | 55 | 1 | Unreviewed; inventory only |
| [lotuswordpro/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/lotuswordpro) | 417 | 1 | Unreviewed; inventory only |
| [m4/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/m4) | 15 | 0 | Unreviewed; inventory only |
| [msicreator/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/msicreator) | 2 | 0 | Unreviewed; inventory only |
| [nlpsolver/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/nlpsolver) | 57 | 1 | Unreviewed; inventory only |
| [o3tl/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/o3tl) | 21 | 1 | Unreviewed; inventory only |
| [odk/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/odk) | 719 | 1 | Unreviewed; inventory only |
| [offapi/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/offapi) | 3,970 | 1 | Unreviewed; inventory only |
| [officecfg/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/officecfg) | 200 | 1 | Unreviewed; inventory only |
| [oovbaapi/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/oovbaapi) | 1,066 | 1 | Unreviewed; inventory only |
| [oox/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/oox) | 556 | 1 | Unreviewed; inventory only |
| [opencl/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/opencl) | 15 | 1 | Unreviewed; inventory only |
| [osx/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/osx) | 2 | 0 | Unreviewed; inventory only |
| [package/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/package) | 150 | 1 | Unreviewed; inventory only |
| [pch/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/pch) | 8 | 1 | Unreviewed; inventory only |
| [postprocess/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/postprocess) | 19 | 1 | Unreviewed; inventory only |
| [pyuno/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/pyuno) | 70 | 1 | Unreviewed; inventory only |
| [qadevOOo/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/qadevOOo) | 1,921 | 1 | Unreviewed; inventory only |
| [readlicense_oo/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/readlicense_oo) | 15 | 1 | Unreviewed; inventory only |
| [registry/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/registry) | 25 | 1 | Unreviewed; inventory only |
| [remotebridges/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/remotebridges) | 6 | 1 | Unreviewed; inventory only |
| [reportbuilder/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/reportbuilder) | 197 | 1 | Unreviewed; inventory only |
| [reportdesign/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/reportdesign) | 269 | 1 | Unreviewed; inventory only |
| [ridljar/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/ridljar) | 156 | 1 | Unreviewed; inventory only |
| [sal/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/sal) | 331 | 1 | Unreviewed; inventory only |
| [salhelper/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/salhelper) | 28 | 1 | Unreviewed; inventory only |
| [sax/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/sax) | 45 | 1 | Unreviewed; inventory only |
| [sc/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/sc) | 4,662 | 1 | Unreviewed; inventory only |
| [scaddins/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/scaddins) | 42 | 1 | Unreviewed; inventory only |
| [sccomp/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/sccomp) | 24 | 1 | Unreviewed; inventory only |
| [schema/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/schema) | 53 | 0 | Unreviewed; inventory only |
| [scp2/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/scp2) | 157 | 1 | Unreviewed; inventory only |
| [scripting/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/scripting) | 197 | 1 | Unreviewed; inventory only |
| [sd/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/sd) | 2,057 | 1 | Unreviewed; inventory only |
| [sdext/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/sdext) | 127 | 1 | Unreviewed; inventory only |
| [setup_native/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/setup_native) | 88 | 1 | Unreviewed; inventory only |
| [sfx2/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/sfx2) | 486 | 1 | Unreviewed; inventory only |
| [shell/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/shell) | 184 | 1 | Unreviewed; inventory only |
| [slideshow/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/slideshow) | 296 | 1 | Unreviewed; inventory only |
| [smoketest/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/smoketest) | 35 | 1 | Unreviewed; inventory only |
| [solenv/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/solenv) | 401 | 2 | Selected gbuild module orchestration; other tooling unreviewed |
| [soltools/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/soltools) | 30 | 1 | Unreviewed; inventory only |
| [sot/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/sot) | 53 | 1 | Unreviewed; inventory only |
| [starmath/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/starmath) | 170 | 1 | Unreviewed; inventory only |
| [static/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/static) | 26 | 1 | Unreviewed; inventory only |
| [stoc/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/stoc) | 111 | 1 | Unreviewed; inventory only |
| [store/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/store) | 29 | 1 | Unreviewed; inventory only |
| [svgio/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/svgio) | 225 | 1 | Unreviewed; inventory only |
| [svl/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/svl) | 135 | 1 | Unreviewed; inventory only |
| [svtools/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/svtools) | 161 | 1 | Unreviewed; inventory only |
| [svx/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/svx) | 1,147 | 1 | Unreviewed; inventory only |
| [sw/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/sw) | 7,708 | 1 | Unreviewed; inventory only |
| [swext/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/swext) | 46 | 1 | Unreviewed; inventory only |
| [sysui/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/sysui) | 769 | 1 | Unreviewed; inventory only |
| [test/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/test) | 237 | 1 | Unreviewed; inventory only |
| [testtools/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/testtools) | 85 | 1 | Unreviewed; inventory only |
| [toolkit/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/toolkit) | 246 | 1 | Unreviewed; inventory only |
| [tools/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/tools) | 89 | 1 | Unreviewed; inventory only |
| [ucb/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/ucb) | 263 | 1 | Unreviewed; inventory only |
| [ucbhelper/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/ucbhelper) | 31 | 1 | Unreviewed; inventory only |
| [udkapi/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/udkapi) | 422 | 1 | Unreviewed; inventory only |
| [uitest/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/uitest) | 64 | 1 | Unreviewed; inventory only |
| [unodevtools/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/unodevtools) | 16 | 1 | Unreviewed; inventory only |
| [unoidl/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/unoidl) | 34 | 1 | Unreviewed; inventory only |
| [unoil/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/unoil) | 11 | 1 | Unreviewed; inventory only |
| [unotest/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/unotest) | 37 | 1 | Unreviewed; inventory only |
| [unotools/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/unotools) | 79 | 1 | Unreviewed; inventory only |
| [unoxml/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/unoxml) | 83 | 1 | Unreviewed; inventory only |
| [ure/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/ure) | 28 | 1 | Unreviewed; inventory only |
| [uui/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/uui) | 75 | 1 | Unreviewed; inventory only |
| [vbahelper/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/vbahelper) | 87 | 1 | Unreviewed; inventory only |
| [vcl/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl) | 2,758 | 1 | Selected [VCL/Skia contracts](VCL_SKIA_CONTRACTS.md); other APIs unreviewed |
| [winaccessibility/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/winaccessibility) | 91 | 1 | Unreviewed; inventory only |
| [wizards/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/wizards) | 442 | 1 | Unreviewed; inventory only |
| [writerperfect/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/writerperfect) | 433 | 1 | Unreviewed; inventory only |
| [xmerge/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/xmerge) | 122 | 1 | Unreviewed; inventory only |
| [xmlhelp/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/xmlhelp) | 41 | 1 | Unreviewed; inventory only |
| [xmloff/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/xmloff) | 761 | 1 | Unreviewed; inventory only |
| [xmlreader/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/xmlreader) | 8 | 1 | Unreviewed; inventory only |
| [xmlscript/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/xmlscript) | 39 | 1 | Unreviewed; inventory only |
| [xmlsecurity/](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/tree/38f3847c224e4d735a199e596b11b0a1cf9488e5/xmlsecurity) | 702 | 1 | Unreviewed; inventory only |

## Root files and repository custody

Root files are separately inventoried so build scripts, instructions, licenses,
and configuration are not silently dropped from the boundary. Existing files
are retained; their appearance here does not mean their full content was reviewed.
No `AGENTS.md` or `CLAUDE.md` exists anywhere in the inventoried baseline tree.

- [.buckconfig](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/.buckconfig)
- [.buckversion](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/.buckversion)
- [.clang-format](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/.clang-format)
- [.editorconfig](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/.editorconfig)
- [.git-blame-ignore-revs](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/.git-blame-ignore-revs)
- [.gitattributes](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/.gitattributes)
- [.gitignore](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/.gitignore)
- [.gitmodules](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/.gitmodules)
- [.gitpod.dockerfile](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/.gitpod.dockerfile)
- [.gitpod.yml](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/.gitpod.yml)
- [.gitreview](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/.gitreview)
- [BUCK](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/BUCK)
- [COPYING](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/COPYING)
- [COPYING.LGPL](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/COPYING.LGPL)
- [COPYING.MPL](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/COPYING.MPL)
- [Library_merged.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/Library_merged.mk)
- [Makefile.fetch](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/Makefile.fetch)
- [Makefile.gbuild](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/Makefile.gbuild)
- [Makefile.in](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/Makefile.in)
- [README.Solaris](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/README.Solaris)
- [README.cross](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/README.cross)
- [README.help.md](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/README.help.md)
- [README.md](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/README.md)
- [Repository.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/Repository.mk)
- [RepositoryExternal.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/RepositoryExternal.mk)
- [RepositoryFixes.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/RepositoryFixes.mk)
- [RepositoryModule_build.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/RepositoryModule_build.mk)
- [RepositoryModule_host.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/RepositoryModule_host.mk)
- [TEMPLATE.SOURCECODE.HEADER](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/TEMPLATE.SOURCECODE.HEADER)
- [antivirusDetection.vbs](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/antivirusDetection.vbs)
- [autogen.sh](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/autogen.sh)
- [config.guess](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/config.guess)
- [config.sub](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/config.sub)
- [config_host.mk.in](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/config_host.mk.in)
- [config_host_lang.mk.in](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/config_host_lang.mk.in)
- [configure.ac](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/configure.ac)
- [cpp.hint](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/cpp.hint)
- [download.lst](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/download.lst)
- [g](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/g)
- [install-sh](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/install-sh)
- [install_deps.sh](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/install_deps.sh)
- [leak-suppress.txt](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/leak-suppress.txt)
- [logerrit](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/logerrit)
- [sanitize-ubsan-excludelist](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/sanitize-ubsan-excludelist)
- [setup.cfg](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/setup.cfg)
- [tsan-suppress.txt](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/tsan-suppress.txt)

## Separate submodule repositories

The three gitlinks are tracked boundaries, not expanded content. The relative
URLs are reproduced from the baseline `.gitmodules`; no remote repository
availability or license compatibility is inferred from them. Branch `.` in
that file is configuration metadata, not the pinned contents used by this tree.

| Path | Pinned gitlink commit | `.gitmodules` URL | Coverage |
| --- | --- | --- | --- |
| `dictionaries` | `7272a82714ca91947b4573c09bce4938861a9877` | `../dictionaries` | Contents and package/module contracts unexpanded |
| `helpcontent2` | `1eb2e622fbd81928bc7e8b48f75332c787c01225` | `../help` | Contents and package/module contracts unexpanded |
| `translations` | `fbbd7b927a869cfe63dfbf0542b967da94eef28e` | `../translations` | Contents and package/module contracts unexpanded |

Source: [.gitmodules](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/.gitmodules). These three repositories remain unresolved included boundaries; they are not silently excluded or counted as documented.

## Other discovered build or language-module boundaries

The following exact path inventory supplements gbuild. Bodies and semantic
contracts are unreviewed. It is based on the listed filename conventions, not a
claim that no other custom build system exists.

- [BUCK](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/BUCK)
- [android/source/build.gradle](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/android/source/build.gradle)
- [bean/BUCK](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/bean/BUCK)
- [javaunohelper/BUCK](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/javaunohelper/BUCK)
- [jurt/BUCK](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/jurt/BUCK)
- [ridljar/BUCK](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/ridljar/BUCK)
- [ridljar/source/libreoffice/module-info.java](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/ridljar/source/libreoffice/module-info.java)
- [ridljar/source/unoloader/BUCK](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/ridljar/source/unoloader/BUCK)
- [ridljar/source/unoloader/module-info.java](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/ridljar/source/unoloader/module-info.java)
- [solenv/maven/BUCK](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/solenv/maven/BUCK)
- [uitest/packaging/setup.py](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/uitest/packaging/setup.py)
- [unoil/BUCK](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/unoil/BUCK)

The complete baseline includes 2,574 `.java` and 5,519 `.idl` paths. Those are
source-file counts, not verified namespace counts: their package/module
statements and public APIs have not been exhaustively read. C++, Python, C#,
JavaScript, and other language boundaries likewise remain to be extracted from
source declarations. Public headers, generated interfaces, test-only namespaces,
examples, SDK material, and third-party archives must retain their distinct
roles in a later semantic pass.
