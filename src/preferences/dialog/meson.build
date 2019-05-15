src_mixxx += files([
    './dlgprefautodj.cpp',
    './dlgprefbeats.cpp',
    './dlgprefcrossfader.cpp',
    './dlgprefdeck.cpp',
    './dlgprefeffects.cpp',
    './dlgprefeq.cpp',
    './dlgpreferences.cpp',
    './dlgprefinterface.cpp',
    './dlgprefkey.cpp',
    './dlgpreflibrary.cpp',
    './dlgprefnovinyl.cpp',
    './dlgprefrecord.cpp',
    './dlgprefreplaygain.cpp',
    './dlgprefsound.cpp',
    './dlgprefsounditem.cpp',
    './dlgprefwaveform.cpp'
])

src_ui_files += files([
    './dlgprefautodjdlg.ui',
    './dlgprefbeatsdlg.ui',
    './dlgprefcrossfaderdlg.ui',
    './dlgprefdeckdlg.ui',
    './dlgprefeffectsdlg.ui',
    './dlgprefeqdlg.ui',
    './dlgpreferencesdlg.ui',
    './dlgprefinterfacedlg.ui',
    './dlgprefkeydlg.ui',
    './dlgpreflibrarydlg.ui',
    './dlgprefnovinyldlg.ui',
    './dlgprefrecorddlg.ui',
    './dlgprefreplaygaindlg.ui',
    './dlgprefsounddlg.ui',
    './dlgprefsounditem.ui',
    './dlgprefwaveformdlg.ui'
])


if get_option('FEATURE_VINYLCONTROL')
    src_mixxx += files('./dlgprefvinyl.cpp')
    src_ui_files += files('./dlgprefvinyldlg.ui')
endif

if get_option('FEATURE_MODPLUG')
    src_mixxx += files('./dlgprefmodplug.cpp')
    src_ui_files += files('./dlgprefmodplugdlg.ui')
endif

if get_option('FEATURE_BROADCASTING')
    src_mixxx += files('./dlgprefbroadcast.cpp')
    src_ui_files += files('./dlgprefbroadcastdlg.ui')
endif

if FEATURE_LV2
    src_mixxx += files('./dlgpreflv2.cpp')
    src_ui_files += files('./dlgpreflv2dlg.ui')
endif
