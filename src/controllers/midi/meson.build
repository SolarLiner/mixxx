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

if host_machine.system() == 'windows' or host_machine.system() == 'darwin'
    src_mixxx += files([
        './hss1394controller.cpp',
        './hss1394enumerator.cpp'
    ])
endif
