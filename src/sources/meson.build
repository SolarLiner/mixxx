src_mixxx += files([
    './audiosource.cpp',
    './audiosourcestereoproxy.cpp',
    './libfaadloader.cpp',
    './metadatasourcetaglib.cpp',
    './soundsource.cpp',
    './soundsourceffmpeg.cpp',
    './soundsourceflac.cpp',
    './soundsourcemodplug.cpp',
    './soundsourceoggvorbis.cpp',
    './soundsourceopus.cpp',
    './soundsourceproviderregistry.cpp',
    './soundsourceproxy.cpp',
    './soundsourcesndfile.cpp',
    './soundsourcewv.cpp'
])

if get_option('FEATURE_COREAUDIO')
    subdir('v1')
    src_mixxx += files('./soundsourcecoreaudio.cpp')
endif

if get_option('FEATURE_MEDIAFOUNDATION')
    src_mixxx += files('./soundsourcemediafoundation.cpp')
endif

if get_option('FEATURE_MAD')
    src_mixxx += files('./soundsourcemp3.cpp')
endif

if get_option('FEATURE_MP4')
    src_mixxx += files('./soundsourcem4a.cpp')
endif
