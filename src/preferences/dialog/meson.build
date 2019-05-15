src_mixxx += files([
    './dlgprefautodj.cpp',
    './dlgprefbeats.cpp',
    './dlgprefbroadcast.cpp',
    './dlgprefcrossfader.cpp',
    './dlgprefdeck.cpp',
    './dlgprefeffects.cpp',
    './dlgprefeq.cpp',
    './dlgpreferences.cpp',
    './dlgprefinterface.cpp',
    './dlgprefkey.cpp',
    './dlgpreflibrary.cpp',
    './dlgpreflv2.cpp',
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
    './dlgprefbroadcastdlg.ui',
    './dlgprefcrossfaderdlg.ui',
    './dlgprefdeckdlg.ui',
    './dlgprefeffectsdlg.ui',
    './dlgprefeqdlg.ui',
    './dlgpreferencesdlg.ui',
    './dlgprefinterfacedlg.ui',
    './dlgprefkeydlg.ui',
    './dlgpreflibrarydlg.ui',
    './dlgpreflv2dlg.ui',
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
