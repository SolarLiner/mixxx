src_mixxx += files([
    './midicontroller.cpp',
    './midicontrollerpresetfilehandler.cpp',
    './midienumerator.cpp',
    './midimessage.cpp',
    './midioutputhandler.cpp',
    './midiutils.cpp',
    './portmidicontroller.cpp',
    './portmidienumerator.cpp'
])

if get_option('FEATURE_HSS1394') and ['windows', 'darwin'].contains(host_machine.system())
    src_mixxx += files([
        './hss1394controller.cpp',
        './hss1394enumerator.cpp'
    ])
endif
