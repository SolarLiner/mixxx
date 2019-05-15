src_mixxx += files([
    './encoderbroadcastsettings.cpp',
    './encoder.cpp',
    './encoderflacsettings.cpp',
    './encodermp3.cpp',
    './encodermp3settings.cpp',
    './encoderopus.cpp',
    './encoderopussettings.cpp',
    './encodersndfileflac.cpp',
    './encodervorbis.cpp',
    './encodervorbissettings.cpp',
    './encoderwave.cpp',
    './encoderwavesettings.cpp'
])

if get_option('FEATURE_FFMPEG')
    src_mixxx += files([
        './encoderffmpegcore.cpp',
        './encoderffmpegresample.cpp',
        './encoderffmpegmp3.cpp',
        './encoderffmpegvorbis.cpp'
    ])
endif
