# Module-definition path inventory

[Build and root index](MODULE_INDEX.md) · [Coverage](COVERAGE.md)

Baseline: `38f3847c224e4d735a199e596b11b0a1cf9488e5`.

This is the complete list of 230 tracked paths matching `Module_*.mk` in the
superproject. A filename is discovery evidence for a candidate build boundary;
it does not prove the declared module name, its active configuration, dependencies,
exports, or substantive documentation coverage. The root `RepositoryModule_host.mk`
and `RepositoryModule_build.mk` aggregates are described separately in the
[build index](MODULE_INDEX.md#how-the-build-boundaries-fit-together).

Two candidate bodies are reviewed here: `vcl/Module_vcl.mk` and
`external/skia/Module_skia.mk`. All other 228 bodies and their per-module/package
semantics remain unreviewed in this pass. The `solenv/qa/python/selftest` path
is a build-system self-test location, not an assumed production module. All
external module candidates require their own source, build and provenance review;
a directory name is not a third-party version or licensing claim.

## Inherited top-level candidate definitions

| Exact manifest path | Review status |
| --- | --- |
| [UnoControls/Module_UnoControls.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/UnoControls/Module_UnoControls.mk) | Body and semantic contracts unreviewed |
| [accessibility/Module_accessibility.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/accessibility/Module_accessibility.mk) | Body and semantic contracts unreviewed |
| [android/Module_android.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/android/Module_android.mk) | Body and semantic contracts unreviewed |
| [animations/Module_animations.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/animations/Module_animations.mk) | Body and semantic contracts unreviewed |
| [apple_remote/Module_apple_remote.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/apple_remote/Module_apple_remote.mk) | Body and semantic contracts unreviewed |
| [avmedia/Module_avmedia.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/avmedia/Module_avmedia.mk) | Body and semantic contracts unreviewed |
| [basctl/Module_basctl.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/basctl/Module_basctl.mk) | Body and semantic contracts unreviewed |
| [basegfx/Module_basegfx.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/basegfx/Module_basegfx.mk) | Body and semantic contracts unreviewed |
| [basic/Module_basic.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/basic/Module_basic.mk) | Body and semantic contracts unreviewed |
| [bean/Module_bean.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/bean/Module_bean.mk) | Body and semantic contracts unreviewed |
| [binaryurp/Module_binaryurp.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/binaryurp/Module_binaryurp.mk) | Body and semantic contracts unreviewed |
| [bridges/Module_bridges.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/bridges/Module_bridges.mk) | Body and semantic contracts unreviewed |
| [canvas/Module_canvas.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/canvas/Module_canvas.mk) | Body and semantic contracts unreviewed |
| [chart2/Module_chart2.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/chart2/Module_chart2.mk) | Body and semantic contracts unreviewed |
| [cli_ure/Module_cli_ure.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/cli_ure/Module_cli_ure.mk) | Body and semantic contracts unreviewed |
| [codemaker/Module_codemaker.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/codemaker/Module_codemaker.mk) | Body and semantic contracts unreviewed |
| [comphelper/Module_comphelper.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/comphelper/Module_comphelper.mk) | Body and semantic contracts unreviewed |
| [configmgr/Module_configmgr.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/configmgr/Module_configmgr.mk) | Body and semantic contracts unreviewed |
| [connectivity/Module_connectivity.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/connectivity/Module_connectivity.mk) | Body and semantic contracts unreviewed |
| [cppcanvas/Module_cppcanvas.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/cppcanvas/Module_cppcanvas.mk) | Body and semantic contracts unreviewed |
| [cppu/Module_cppu.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/cppu/Module_cppu.mk) | Body and semantic contracts unreviewed |
| [cppuhelper/Module_cppuhelper.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/cppuhelper/Module_cppuhelper.mk) | Body and semantic contracts unreviewed |
| [cpputools/Module_cpputools.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/cpputools/Module_cpputools.mk) | Body and semantic contracts unreviewed |
| [cui/Module_cui.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/cui/Module_cui.mk) | Body and semantic contracts unreviewed |
| [dbaccess/Module_dbaccess.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/dbaccess/Module_dbaccess.mk) | Body and semantic contracts unreviewed |
| [desktop/Module_desktop.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/desktop/Module_desktop.mk) | Body and semantic contracts unreviewed |
| [docmodel/Module_docmodel.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/docmodel/Module_docmodel.mk) | Body and semantic contracts unreviewed |
| [drawinglayer/Module_drawinglayer.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/drawinglayer/Module_drawinglayer.mk) | Body and semantic contracts unreviewed |
| [editeng/Module_editeng.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/editeng/Module_editeng.mk) | Body and semantic contracts unreviewed |
| [embeddedobj/Module_embeddedobj.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/embeddedobj/Module_embeddedobj.mk) | Body and semantic contracts unreviewed |
| [embedserv/Module_embedserv.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/embedserv/Module_embedserv.mk) | Body and semantic contracts unreviewed |
| [emfio/Module_emfio.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/emfio/Module_emfio.mk) | Body and semantic contracts unreviewed |
| [eventattacher/Module_eventattacher.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/eventattacher/Module_eventattacher.mk) | Body and semantic contracts unreviewed |
| [extensions/Module_extensions.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/extensions/Module_extensions.mk) | Body and semantic contracts unreviewed |
| [extras/Module_extras.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/extras/Module_extras.mk) | Body and semantic contracts unreviewed |
| [filter/Module_filter.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/filter/Module_filter.mk) | Body and semantic contracts unreviewed |
| [forms/Module_forms.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/forms/Module_forms.mk) | Body and semantic contracts unreviewed |
| [formula/Module_formula.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/formula/Module_formula.mk) | Body and semantic contracts unreviewed |
| [fpicker/Module_fpicker.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/fpicker/Module_fpicker.mk) | Body and semantic contracts unreviewed |
| [framework/Module_framework.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/framework/Module_framework.mk) | Body and semantic contracts unreviewed |
| [helpcompiler/Module_helpcompiler.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/helpcompiler/Module_helpcompiler.mk) | Body and semantic contracts unreviewed |
| [hwpfilter/Module_hwpfilter.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/hwpfilter/Module_hwpfilter.mk) | Body and semantic contracts unreviewed |
| [i18nlangtag/Module_i18nlangtag.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/i18nlangtag/Module_i18nlangtag.mk) | Body and semantic contracts unreviewed |
| [i18npool/Module_i18npool.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/i18npool/Module_i18npool.mk) | Body and semantic contracts unreviewed |
| [i18nutil/Module_i18nutil.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/i18nutil/Module_i18nutil.mk) | Body and semantic contracts unreviewed |
| [idl/Module_idl.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/idl/Module_idl.mk) | Body and semantic contracts unreviewed |
| [instsetoo_native/Module_instsetoo_native.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/instsetoo_native/Module_instsetoo_native.mk) | Body and semantic contracts unreviewed |
| [io/Module_io.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/io/Module_io.mk) | Body and semantic contracts unreviewed |
| [ios/Module_ios.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/ios/Module_ios.mk) | Body and semantic contracts unreviewed |
| [javaunohelper/Module_javaunohelper.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/javaunohelper/Module_javaunohelper.mk) | Body and semantic contracts unreviewed |
| [jurt/Module_jurt.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/jurt/Module_jurt.mk) | Body and semantic contracts unreviewed |
| [jvmaccess/Module_jvmaccess.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/jvmaccess/Module_jvmaccess.mk) | Body and semantic contracts unreviewed |
| [jvmfwk/Module_jvmfwk.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/jvmfwk/Module_jvmfwk.mk) | Body and semantic contracts unreviewed |
| [l10ntools/Module_l10ntools.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/l10ntools/Module_l10ntools.mk) | Body and semantic contracts unreviewed |
| [librelogo/Module_librelogo.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/librelogo/Module_librelogo.mk) | Body and semantic contracts unreviewed |
| [libreofficekit/Module_libreofficekit.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/libreofficekit/Module_libreofficekit.mk) | Body and semantic contracts unreviewed |
| [lingucomponent/Module_lingucomponent.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/lingucomponent/Module_lingucomponent.mk) | Body and semantic contracts unreviewed |
| [linguistic/Module_linguistic.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/linguistic/Module_linguistic.mk) | Body and semantic contracts unreviewed |
| [lotuswordpro/Module_lotuswordpro.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/lotuswordpro/Module_lotuswordpro.mk) | Body and semantic contracts unreviewed |
| [nlpsolver/Module_nlpsolver.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/nlpsolver/Module_nlpsolver.mk) | Body and semantic contracts unreviewed |
| [o3tl/Module_o3tl.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/o3tl/Module_o3tl.mk) | Body and semantic contracts unreviewed |
| [odk/Module_odk.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/odk/Module_odk.mk) | Body and semantic contracts unreviewed |
| [offapi/Module_offapi.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/offapi/Module_offapi.mk) | Body and semantic contracts unreviewed |
| [officecfg/Module_officecfg.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/officecfg/Module_officecfg.mk) | Body and semantic contracts unreviewed |
| [oovbaapi/Module_oovbaapi.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/oovbaapi/Module_oovbaapi.mk) | Body and semantic contracts unreviewed |
| [oox/Module_oox.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/oox/Module_oox.mk) | Body and semantic contracts unreviewed |
| [opencl/Module_opencl.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/opencl/Module_opencl.mk) | Body and semantic contracts unreviewed |
| [package/Module_package.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/package/Module_package.mk) | Body and semantic contracts unreviewed |
| [pch/Module_pch.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/pch/Module_pch.mk) | Body and semantic contracts unreviewed |
| [postprocess/Module_postprocess.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/postprocess/Module_postprocess.mk) | Body and semantic contracts unreviewed |
| [pyuno/Module_pyuno.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/pyuno/Module_pyuno.mk) | Body and semantic contracts unreviewed |
| [qadevOOo/Module_qadevOOo.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/qadevOOo/Module_qadevOOo.mk) | Body and semantic contracts unreviewed |
| [readlicense_oo/Module_readlicense_oo.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/readlicense_oo/Module_readlicense_oo.mk) | Body and semantic contracts unreviewed |
| [registry/Module_registry.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/registry/Module_registry.mk) | Body and semantic contracts unreviewed |
| [remotebridges/Module_remotebridges.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/remotebridges/Module_remotebridges.mk) | Body and semantic contracts unreviewed |
| [reportbuilder/Module_reportbuilder.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/reportbuilder/Module_reportbuilder.mk) | Body and semantic contracts unreviewed |
| [reportdesign/Module_reportdesign.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/reportdesign/Module_reportdesign.mk) | Body and semantic contracts unreviewed |
| [ridljar/Module_ridljar.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/ridljar/Module_ridljar.mk) | Body and semantic contracts unreviewed |
| [sal/Module_sal.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/sal/Module_sal.mk) | Body and semantic contracts unreviewed |
| [salhelper/Module_salhelper.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/salhelper/Module_salhelper.mk) | Body and semantic contracts unreviewed |
| [sax/Module_sax.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/sax/Module_sax.mk) | Body and semantic contracts unreviewed |
| [sc/Module_sc.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/sc/Module_sc.mk) | Body and semantic contracts unreviewed |
| [scaddins/Module_scaddins.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/scaddins/Module_scaddins.mk) | Body and semantic contracts unreviewed |
| [sccomp/Module_sccomp.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/sccomp/Module_sccomp.mk) | Body and semantic contracts unreviewed |
| [scp2/Module_scp2.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/scp2/Module_scp2.mk) | Body and semantic contracts unreviewed |
| [scripting/Module_scripting.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/scripting/Module_scripting.mk) | Body and semantic contracts unreviewed |
| [sd/Module_sd.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/sd/Module_sd.mk) | Body and semantic contracts unreviewed |
| [sdext/Module_sdext.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/sdext/Module_sdext.mk) | Body and semantic contracts unreviewed |
| [setup_native/Module_setup_native.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/setup_native/Module_setup_native.mk) | Body and semantic contracts unreviewed |
| [sfx2/Module_sfx2.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/sfx2/Module_sfx2.mk) | Body and semantic contracts unreviewed |
| [shell/Module_shell.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/shell/Module_shell.mk) | Body and semantic contracts unreviewed |
| [slideshow/Module_slideshow.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/slideshow/Module_slideshow.mk) | Body and semantic contracts unreviewed |
| [smoketest/Module_smoketest.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/smoketest/Module_smoketest.mk) | Body and semantic contracts unreviewed |
| [solenv/Module_solenv.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/solenv/Module_solenv.mk) | Body and semantic contracts unreviewed |
| [soltools/Module_soltools.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/soltools/Module_soltools.mk) | Body and semantic contracts unreviewed |
| [sot/Module_sot.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/sot/Module_sot.mk) | Body and semantic contracts unreviewed |
| [starmath/Module_starmath.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/starmath/Module_starmath.mk) | Body and semantic contracts unreviewed |
| [static/Module_static.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/static/Module_static.mk) | Body and semantic contracts unreviewed |
| [stoc/Module_stoc.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/stoc/Module_stoc.mk) | Body and semantic contracts unreviewed |
| [store/Module_store.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/store/Module_store.mk) | Body and semantic contracts unreviewed |
| [svgio/Module_svgio.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/svgio/Module_svgio.mk) | Body and semantic contracts unreviewed |
| [svl/Module_svl.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/svl/Module_svl.mk) | Body and semantic contracts unreviewed |
| [svtools/Module_svtools.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/svtools/Module_svtools.mk) | Body and semantic contracts unreviewed |
| [svx/Module_svx.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/svx/Module_svx.mk) | Body and semantic contracts unreviewed |
| [sw/Module_sw.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/sw/Module_sw.mk) | Body and semantic contracts unreviewed |
| [swext/Module_swext.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/swext/Module_swext.mk) | Body and semantic contracts unreviewed |
| [sysui/Module_sysui.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/sysui/Module_sysui.mk) | Body and semantic contracts unreviewed |
| [test/Module_test.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/test/Module_test.mk) | Body and semantic contracts unreviewed |
| [testtools/Module_testtools.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/testtools/Module_testtools.mk) | Body and semantic contracts unreviewed |
| [toolkit/Module_toolkit.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/toolkit/Module_toolkit.mk) | Body and semantic contracts unreviewed |
| [tools/Module_tools.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/tools/Module_tools.mk) | Body and semantic contracts unreviewed |
| [ucb/Module_ucb.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/ucb/Module_ucb.mk) | Body and semantic contracts unreviewed |
| [ucbhelper/Module_ucbhelper.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/ucbhelper/Module_ucbhelper.mk) | Body and semantic contracts unreviewed |
| [udkapi/Module_udkapi.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/udkapi/Module_udkapi.mk) | Body and semantic contracts unreviewed |
| [uitest/Module_uitest.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/uitest/Module_uitest.mk) | Body and semantic contracts unreviewed |
| [unodevtools/Module_unodevtools.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/unodevtools/Module_unodevtools.mk) | Body and semantic contracts unreviewed |
| [unoidl/Module_unoidl.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/unoidl/Module_unoidl.mk) | Body and semantic contracts unreviewed |
| [unoil/Module_unoil.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/unoil/Module_unoil.mk) | Body and semantic contracts unreviewed |
| [unotest/Module_unotest.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/unotest/Module_unotest.mk) | Body and semantic contracts unreviewed |
| [unotools/Module_unotools.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/unotools/Module_unotools.mk) | Body and semantic contracts unreviewed |
| [unoxml/Module_unoxml.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/unoxml/Module_unoxml.mk) | Body and semantic contracts unreviewed |
| [ure/Module_ure.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/ure/Module_ure.mk) | Body and semantic contracts unreviewed |
| [uui/Module_uui.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/uui/Module_uui.mk) | Body and semantic contracts unreviewed |
| [vbahelper/Module_vbahelper.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vbahelper/Module_vbahelper.mk) | Body and semantic contracts unreviewed |
| [vcl/Module_vcl.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/vcl/Module_vcl.mk) | Selected target groups reviewed; full VCL semantics partial |
| [winaccessibility/Module_winaccessibility.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/winaccessibility/Module_winaccessibility.mk) | Body and semantic contracts unreviewed |
| [wizards/Module_wizards.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/wizards/Module_wizards.mk) | Body and semantic contracts unreviewed |
| [writerperfect/Module_writerperfect.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/writerperfect/Module_writerperfect.mk) | Body and semantic contracts unreviewed |
| [xmerge/Module_xmerge.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/xmerge/Module_xmerge.mk) | Body and semantic contracts unreviewed |
| [xmlhelp/Module_xmlhelp.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/xmlhelp/Module_xmlhelp.mk) | Body and semantic contracts unreviewed |
| [xmloff/Module_xmloff.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/xmloff/Module_xmloff.mk) | Body and semantic contracts unreviewed |
| [xmlreader/Module_xmlreader.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/xmlreader/Module_xmlreader.mk) | Body and semantic contracts unreviewed |
| [xmlscript/Module_xmlscript.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/xmlscript/Module_xmlscript.mk) | Body and semantic contracts unreviewed |
| [xmlsecurity/Module_xmlsecurity.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/xmlsecurity/Module_xmlsecurity.mk) | Body and semantic contracts unreviewed |

## External dependency candidate definitions

| Exact manifest path | Review status |
| --- | --- |
| [external/IAccessible2/Module_IAccessible2.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/IAccessible2/Module_IAccessible2.mk) | Body and semantic contracts unreviewed |
| [external/Module_external.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/Module_external.mk) | Body and semantic contracts unreviewed |
| [external/argon2/Module_argon2.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/argon2/Module_argon2.mk) | Body and semantic contracts unreviewed |
| [external/beanshell/Module_beanshell.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/beanshell/Module_beanshell.mk) | Body and semantic contracts unreviewed |
| [external/boost/Module_boost.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/boost/Module_boost.mk) | Body and semantic contracts unreviewed |
| [external/box2d/Module_box2d.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/box2d/Module_box2d.mk) | Body and semantic contracts unreviewed |
| [external/breakpad/Module_breakpad.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/breakpad/Module_breakpad.mk) | Body and semantic contracts unreviewed |
| [external/bzip2/Module_bzip2.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/bzip2/Module_bzip2.mk) | Body and semantic contracts unreviewed |
| [external/cairo/Module_cairo.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/cairo/Module_cairo.mk) | Body and semantic contracts unreviewed |
| [external/clew/Module_clew.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/clew/Module_clew.mk) | Body and semantic contracts unreviewed |
| [external/clucene/Module_clucene.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/clucene/Module_clucene.mk) | Body and semantic contracts unreviewed |
| [external/coinmp/Module_coinmp.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/coinmp/Module_coinmp.mk) | Body and semantic contracts unreviewed |
| [external/cppunit/Module_cppunit.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/cppunit/Module_cppunit.mk) | Body and semantic contracts unreviewed |
| [external/curl/Module_curl.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/curl/Module_curl.mk) | Body and semantic contracts unreviewed |
| [external/dragonbox/Module_dragonbox.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/dragonbox/Module_dragonbox.mk) | Body and semantic contracts unreviewed |
| [external/dtoa/Module_dtoa.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/dtoa/Module_dtoa.mk) | Body and semantic contracts unreviewed |
| [external/epm/Module_epm.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/epm/Module_epm.mk) | Body and semantic contracts unreviewed |
| [external/epoxy/Module_epoxy.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/epoxy/Module_epoxy.mk) | Body and semantic contracts unreviewed |
| [external/expat/Module_expat.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/expat/Module_expat.mk) | Body and semantic contracts unreviewed |
| [external/firebird/Module_firebird.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/firebird/Module_firebird.mk) | Body and semantic contracts unreviewed |
| [external/fontconfig/Module_fontconfig.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/fontconfig/Module_fontconfig.mk) | Body and semantic contracts unreviewed |
| [external/freetype/Module_freetype.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/freetype/Module_freetype.mk) | Body and semantic contracts unreviewed |
| [external/frozen/Module_frozen.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/frozen/Module_frozen.mk) | Body and semantic contracts unreviewed |
| [external/glm/Module_glm.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/glm/Module_glm.mk) | Body and semantic contracts unreviewed |
| [external/gpgmepp/Module_gpgmepp.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/gpgmepp/Module_gpgmepp.mk) | Body and semantic contracts unreviewed |
| [external/graphite/Module_graphite.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/graphite/Module_graphite.mk) | Body and semantic contracts unreviewed |
| [external/harfbuzz/Module_harfbuzz.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/harfbuzz/Module_harfbuzz.mk) | Body and semantic contracts unreviewed |
| [external/hsqldb/Module_hsqldb.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/hsqldb/Module_hsqldb.mk) | Body and semantic contracts unreviewed |
| [external/hunspell/Module_hunspell.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/hunspell/Module_hunspell.mk) | Body and semantic contracts unreviewed |
| [external/hyphen/Module_hyphen.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/hyphen/Module_hyphen.mk) | Body and semantic contracts unreviewed |
| [external/icu/Module_icu.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/icu/Module_icu.mk) | Body and semantic contracts unreviewed |
| [external/java_websocket/Module_java_websocket.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/java_websocket/Module_java_websocket.mk) | Body and semantic contracts unreviewed |
| [external/jfreereport/Module_jfreereport.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/jfreereport/Module_jfreereport.mk) | Body and semantic contracts unreviewed |
| [external/lcms2/Module_lcms2.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/lcms2/Module_lcms2.mk) | Body and semantic contracts unreviewed |
| [external/libabw/Module_libabw.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libabw/Module_libabw.mk) | Body and semantic contracts unreviewed |
| [external/libassuan/Module_libassuan.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libassuan/Module_libassuan.mk) | Body and semantic contracts unreviewed |
| [external/libatomic_ops/Module_libatomic_ops.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libatomic_ops/Module_libatomic_ops.mk) | Body and semantic contracts unreviewed |
| [external/libcdr/Module_libcdr.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libcdr/Module_libcdr.mk) | Body and semantic contracts unreviewed |
| [external/libcmis/Module_libcmis.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libcmis/Module_libcmis.mk) | Body and semantic contracts unreviewed |
| [external/libebook/Module_libebook.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libebook/Module_libebook.mk) | Body and semantic contracts unreviewed |
| [external/libeot/Module_libeot.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libeot/Module_libeot.mk) | Body and semantic contracts unreviewed |
| [external/libepubgen/Module_libepubgen.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libepubgen/Module_libepubgen.mk) | Body and semantic contracts unreviewed |
| [external/libetonyek/Module_libetonyek.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libetonyek/Module_libetonyek.mk) | Body and semantic contracts unreviewed |
| [external/libexttextcat/Module_libexttextcat.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libexttextcat/Module_libexttextcat.mk) | Body and semantic contracts unreviewed |
| [external/libffi/Module_libffi.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libffi/Module_libffi.mk) | Body and semantic contracts unreviewed |
| [external/libfreehand/Module_libfreehand.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libfreehand/Module_libfreehand.mk) | Body and semantic contracts unreviewed |
| [external/libgpg-error/Module_libgpg-error.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libgpg-error/Module_libgpg-error.mk) | Body and semantic contracts unreviewed |
| [external/libjpeg-turbo/Module_libjpeg-turbo.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libjpeg-turbo/Module_libjpeg-turbo.mk) | Body and semantic contracts unreviewed |
| [external/liblangtag/Module_liblangtag.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/liblangtag/Module_liblangtag.mk) | Body and semantic contracts unreviewed |
| [external/libmspub/Module_libmspub.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libmspub/Module_libmspub.mk) | Body and semantic contracts unreviewed |
| [external/libmwaw/Module_libmwaw.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libmwaw/Module_libmwaw.mk) | Body and semantic contracts unreviewed |
| [external/libnumbertext/Module_libnumbertext.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libnumbertext/Module_libnumbertext.mk) | Body and semantic contracts unreviewed |
| [external/libodfgen/Module_libodfgen.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libodfgen/Module_libodfgen.mk) | Body and semantic contracts unreviewed |
| [external/liborcus/Module_liborcus.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/liborcus/Module_liborcus.mk) | Body and semantic contracts unreviewed |
| [external/libpagemaker/Module_libpagemaker.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libpagemaker/Module_libpagemaker.mk) | Body and semantic contracts unreviewed |
| [external/libpng/Module_libpng.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libpng/Module_libpng.mk) | Body and semantic contracts unreviewed |
| [external/libqxp/Module_libqxp.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libqxp/Module_libqxp.mk) | Body and semantic contracts unreviewed |
| [external/librevenge/Module_librevenge.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/librevenge/Module_librevenge.mk) | Body and semantic contracts unreviewed |
| [external/libstaroffice/Module_libstaroffice.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libstaroffice/Module_libstaroffice.mk) | Body and semantic contracts unreviewed |
| [external/libtiff/Module_libtiff.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libtiff/Module_libtiff.mk) | Body and semantic contracts unreviewed |
| [external/libtommath/Module_libtommath.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libtommath/Module_libtommath.mk) | Body and semantic contracts unreviewed |
| [external/libvisio/Module_libvisio.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libvisio/Module_libvisio.mk) | Body and semantic contracts unreviewed |
| [external/libwebp/Module_libwebp.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libwebp/Module_libwebp.mk) | Body and semantic contracts unreviewed |
| [external/libwpd/Module_libwpd.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libwpd/Module_libwpd.mk) | Body and semantic contracts unreviewed |
| [external/libwpg/Module_libwpg.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libwpg/Module_libwpg.mk) | Body and semantic contracts unreviewed |
| [external/libwps/Module_libwps.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libwps/Module_libwps.mk) | Body and semantic contracts unreviewed |
| [external/libxml2/Module_libxml2.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libxml2/Module_libxml2.mk) | Body and semantic contracts unreviewed |
| [external/libxslt/Module_libxslt.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libxslt/Module_libxslt.mk) | Body and semantic contracts unreviewed |
| [external/libzmf/Module_libzmf.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/libzmf/Module_libzmf.mk) | Body and semantic contracts unreviewed |
| [external/lpsolve/Module_lpsolve.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/lpsolve/Module_lpsolve.mk) | Body and semantic contracts unreviewed |
| [external/lxml/Module_lxml.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/lxml/Module_lxml.mk) | Body and semantic contracts unreviewed |
| [external/mariadb-connector-c/Module_mariadb-connector-c.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/mariadb-connector-c/Module_mariadb-connector-c.mk) | Body and semantic contracts unreviewed |
| [external/mdds/Module_mdds.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/mdds/Module_mdds.mk) | Body and semantic contracts unreviewed |
| [external/mdnsresponder/Module_mdnsresponder.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/mdnsresponder/Module_mdnsresponder.mk) | Body and semantic contracts unreviewed |
| [external/misc_extensions/Module_misc_extensions.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/misc_extensions/Module_misc_extensions.mk) | Body and semantic contracts unreviewed |
| [external/more_fonts/Module_more_fonts.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/more_fonts/Module_more_fonts.mk) | Body and semantic contracts unreviewed |
| [external/msc-externals/Module_msc-externals.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/msc-externals/Module_msc-externals.mk) | Body and semantic contracts unreviewed |
| [external/mythes/Module_mythes.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/mythes/Module_mythes.mk) | Body and semantic contracts unreviewed |
| [external/nss/Module_nss.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/nss/Module_nss.mk) | Body and semantic contracts unreviewed |
| [external/onlineupdate/Module_onlineupdate.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/onlineupdate/Module_onlineupdate.mk) | Body and semantic contracts unreviewed |
| [external/openldap/Module_openldap.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/openldap/Module_openldap.mk) | Body and semantic contracts unreviewed |
| [external/openssl/Module_openssl.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/openssl/Module_openssl.mk) | Body and semantic contracts unreviewed |
| [external/pdfium/Module_pdfium.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/pdfium/Module_pdfium.mk) | Body and semantic contracts unreviewed |
| [external/poppler/Module_poppler.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/poppler/Module_poppler.mk) | Body and semantic contracts unreviewed |
| [external/postgresql/Module_postgresql.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/postgresql/Module_postgresql.mk) | Body and semantic contracts unreviewed |
| [external/python3/Module_python3.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/python3/Module_python3.mk) | Body and semantic contracts unreviewed |
| [external/redland/Module_redland.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/redland/Module_redland.mk) | Body and semantic contracts unreviewed |
| [external/rhino/Module_rhino.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/rhino/Module_rhino.mk) | Body and semantic contracts unreviewed |
| [external/skia/Module_skia.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/skia/Module_skia.mk) | Registers UnpackedTarball_skia and Library_skia; other semantics partial |
| [external/twain_dsm/Module_twain_dsm.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/twain_dsm/Module_twain_dsm.mk) | Body and semantic contracts unreviewed |
| [external/xmlsec/Module_xmlsec.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/xmlsec/Module_xmlsec.mk) | Body and semantic contracts unreviewed |
| [external/xsltml/Module_xsltml.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/xsltml/Module_xsltml.mk) | Body and semantic contracts unreviewed |
| [external/zlib/Module_zlib.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/zlib/Module_zlib.mk) | Body and semantic contracts unreviewed |
| [external/zxcvbn-c/Module_zxcvbn-c.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/zxcvbn-c/Module_zxcvbn-c.mk) | Body and semantic contracts unreviewed |
| [external/zxing/Module_zxing.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/external/zxing/Module_zxing.mk) | Body and semantic contracts unreviewed |

## Other nested candidate definitions

| Exact manifest path | Review status |
| --- | --- |
| [solenv/qa/python/selftest/Module_selftest.mk](https://github.com/hsoliwal/initiative31-prototype-skiavcl-libreoffice/blob/38f3847c224e4d735a199e596b11b0a1cf9488e5/solenv/qa/python/selftest/Module_selftest.mk) | Body and semantic contracts unreviewed |

## Target-definition counts are a different denominator

The inventory contains 2,485 `.mk` paths in total. The counts below match the
filename prefix, not macro expansion, configuration selection, independent
projects, or tests that have run. They include inherited examples, fixtures,
and support files wherever that naming pattern occurs.

| Filename pattern | Tracked paths |
| --- | ---: |
| `Library_*.mk` | 336 |
| `Executable_*.mk` | 149 |
| `StaticLibrary_*.mk` | 56 |
| `CppunitTest_*.mk` | 567 |
| `JunitTest_*.mk` | 60 |
| `PythonTest_*.mk` | 11 |
| `UITest_*.mk` | 73 |
| `Package_*.mk` | 142 |
| `ExternalPackage_*.mk` | 82 |
| `GeneratedPackage_*.mk` | 5 |
| `UnpackedTarball_*.mk` | 131 |
| `ExternalProject_*.mk` | 80 |
| `Jar_*.mk` | 37 |
| `UnoApi_*.mk` | 3 |
| `InternalUnoApi_*.mk` | 7 |
| `UIConfig_*.mk` | 39 |
| `CustomTarget_*.mk` | 100 |

These target files are not separately explained by this inventory. Their bodies,
inputs, outputs, dependencies, configuration guards, generated artifacts, and
public contracts remain open unless a selected reference page explicitly reviews
them. The 142 `Package_*.mk` paths must not be reported as 142 documented language
packages. Likewise, the 567 `CppunitTest_*.mk` paths do not represent 567 passing
tests.
