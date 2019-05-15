src_mixxx += files([
    './battery.cpp',
])

if host_machine.system() == 'linux'
    src_mixxx += files('./batterylinux.cpp')
elif host_machine.system() == 'darwin'
    src_mixxx += files('./batterymac.cpp')
elif host_machine.system() == 'windows'
    src_mixxx += files('./batterywindows.cpp')
endif
