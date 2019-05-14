src_mixxx += files([
    './audiosource.cpp',
    './audiosourcestereoproxy.cpp',
    './libfaadloader.cpp',
    './metadatasourcetaglib.cpp',
    './soundsource.cpp',
    './soundsourceffmpeg.cpp',
    './soundsourceflac.cpp',
    './soundsourcem4a.cpp',
    './soundsourcemodplug.cpp',
    './soundsourcemp3.cpp',
    './soundsourceoggvorbis.cpp',
    './soundsourceopus.cpp',
    './soundsourceproviderregistry.cpp',
    './soundsourceproxy.cpp',
    './soundsourcesndfile.cpp',
    './soundsourcewv.cpp'
])

if host_machine.system() == 'darwin'
    src_mixxx += files('./soundsourcecoreaudio.cpp')
elif host_machine.system() == 'windows'
    src_mixxx += files('./soundsourcemediafoundation.cpp')
endif

subdir('v1')
