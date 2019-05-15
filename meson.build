project('mixxx', 'c', 'cpp', version: '2.3.0a-pre', default_options:['cpp_std=c++11'])

# Get compiler for future reference
cc = meson.get_compiler('cpp')

# Utils
git_exe = find_program('git')

# Modules
qt5_mod = import('qt5')

# Dependencies
m_dep = cc.find_library('m')
threads_dep = dependency('threads', required: false)
opus_dep = dependency('opus')
qt5_dep = dependency('qt5', modules: [
    'Core',
    'Concurrent',
    'DBus',
    'Gui',
    'Network',
    'OpenGL',
    'Script',
    'ScriptTools',
    'Sql',
    'Svg',
    'Widgets',
    'Xml'
])
protobuf_dep = dependency('protobuf')

id3tag_dep = dependency('id3tag')
lilv_dep = dependency('lilv-0', required: get_option('FEATURE_LV2'))
ogg_dep = dependency('ogg')
portaudio_dep = dependency('portaudio-2.0')
upower_dep = dependency('upower-glib', required: host_machine.system() == 'linux')
vorbis_dep = dependency('vorbis')
vorbisenc_dep = dependency('vorbisenc')
x11_dep = dependency('x11', required: host_machine.system() == 'linux')

# Subprojects
fidlib_dep = subproject('fidlib').get_variable('fidlib_dep')
pa_ringbuf_dep = subproject('pa-ringbuffer').get_variable('pa_ringbuffer_dep')
libebur128_dep = subproject('libebur128').get_variable('ebur128_dep')
gtest_dep = subproject('gtest-1.7.0').get_variable('gtest_mainless_dep')
qm_dsp_dep = subproject('qm-dsp').get_variable('qm_dsp_dep')
qtscript_bytearray_dep = subproject('qtscript-bytearray').get_variable('qtscript_bytearray_dep')
replaygain_dep = subproject('replaygain').get_variable('replaygain_dep')
soundtouch_dep = subproject('soundtouch').get_variable('soundtouch_dep')

common_deps = [
    m_dep,
    threads_dep,
    opus_dep,
    qt5_dep,
    id3tag_dep,
    lilv_dep,
    ogg_dep,
    portaudio_dep,
    upower_dep,
    vorbis_dep,
    vorbisenc_dep,
    x11_dep,
    fidlib_dep,
    pa_ringbuf_dep,
    libebur128_dep,
    gtest_dep,
    qm_dsp_dep,
    qtscript_bytearray_dep,
    replaygain_dep,
    soundtouch_dep
]

# includes
inc_project = include_directories('src', 'lib')

# Optional features
if get_option('FEATURE_OPENGLES')
    add_project_arguments('-D__OPENGLES__', language: 'cpp')
endif

FEATURE_HSS1394 = get_option('FEATURE_HSS1394') and ['windows', 'darwin'].contains(host_machine.system())
if FEATURE_HSS1394
    common_deps += dependency('hss1394', required: is_available)
endif

FEATURE_HID = get_option('FEATURE_HID') and host_machine.system() == 'linux'
if FEATURE_HID
    hid_dep = dependency('hidapi-libusb', fallback: ['hidapi-0.8.0-rc1', 'hidapi_dep'])
    common_deps += hid_dep
    add_project_arguments('-D__HID__', language: 'cpp')
endif

FEATURE_BULK = get_option('FEATURE_BULK') and host_machine.system() == 'linux'
if FEATURE_BULK
    common_deps += dependency('libusb-1.0')
endif

FEATURE_MAD = get_option('FEATURE_MAD') and host_machine.system() == 'darwin'
if FEATURE_MAD
    common_deps += [dependency('mad'), dependency('id3tag')]
endif

FEATURE_COREAUDIO = get_option('FEATURE_COREAUDIO') and host_machine.system() == 'darwin'
if FEATURE_COREAUDIO
    common_deps += [dependency('AudioToolbox'), dependency('CoreFoundation')]
    add_project_arguments('-D__COREAUDIO__', language: 'cpp')
endif

FEATURE_MEDIAFOUNDATION = get_option('FEATURE_MEDIAFOUNDATION') and host_machine.system() == 'windows'
if FEATURE_MEDIAFOUNDATION
    foreach lib : ['Ole32', 'Mfuuid', 'Mfplat', 'Mfreadwrite']
        common_deps += cc.find_library(lib)
    endforeach
    add_project_arguments('-D__MEDIAFOUNDATION__', language: 'cpp')
endif

if get_option('FEATURE_VINYLCONTROL')
    common_deps += subproject('xwax').get_variable('xwax_dep')
    add_project_arguments('-D__VINYLCONTROL__', language: 'cpp')
endif

if get_option('FEATURE_MODPLUG')
    common_deps += dependency('libmodplug')
    add_project_arguments('-D__MODPLUG__')
endif

if get_option('FEATURE_FAAD')
    add_project_arguments('-D__FAAD__', language:'cpp')
    libmp4_dep = dependency('mp4v2', required: false)
    if libmp4_dep.found()
        add_project_arguments('-D__MP4V2__', language:'cpp')
    else
        libmp4_dep = dependency('mp4')
    endif
    common_deps += libmp4_dep
endif

if get_option('FEATURE_WAVPACK')
    common_deps += dependency('wavpack')
    add_project_arguments('-D__WV__', language:'cpp')
endif

if get_option('FEATURE_BROADCASTING')
    add_project_arguments('-D__BROADCAST__', language:'cpp')
    common_deps += dependency('shout')
    if host_machine.system() == 'windows'
        foreach lib : ['winmm', 'ws2_32', 'gdi32']
            common_deps += cc.find_library(lib)
        endforeach
    endif
endif

if get_option('FEATURE_OPUS')
    add_project_arguments('-D__OPUS__', language:'cpp')
    common_deps += dependency('opusfile')
    common_deps += dependency('opus')
endif

if get_option('FEATURE_FFMPEG')
        add_project_arguments('-D__STDC_CONSTANT_MACROS', '-D__STD_LIMIT_MACROS', '-D__STD_FORMAT_MACROS', '-D__FFMPEGFILE__', language: 'cpp')
    if ['linux', 'darwin', 'freebsd'].contains(host_machine.system())
        foreach lib : ['libavcodec', 'libavformat', 'libavutil']
            common_deps += dependency(lib)
        endforeach
    else
        foreach lib : ['avcodec', 'avformat', 'avutil', 'z', 'swresample', 'gsm', 'vorbisenc', 'vorbis', 'ogg']
            common_deps += cc.find_library(lib)
        endforeach
    endif
endif
FEATURE_LV2 = get_option('FEATURE_LV2') and ['linux', 'darwin', 'freebsd'].contains(host_machine.system())
if FEATURE_LV2
    add_project_arguments('-D__LILV__', language: 'cpp')
    common_deps += dependency('lilv-0')
endif

FEATURE_BATTERY = get_option('FEATURE_BATTERY') and ['windows', 'linux', 'darwin'].contains(host_machine.system())
if FEATURE_BATTERY
    add_project_arguments('-D__BATTERY__', language:'cpp')
endif

if get_option('FEATURE_QTKEYCHAIN')
    add_project_arguments('-D__QTKEYCHAIN__')
    common_deps += dependency('qt5keychain')
endif

# Other toggleable options
if get_option('ENABLE_PERFTOOLS')
    common_deps += dependency('tcmalloc')
endif
if get_option('ENABLE_ASMLIB')
    # TODO: ASMLIB support
    warning('ASMLIB skipped, no sources to checkout')
endif
if not get_option('ENABLE_BUILDTIME')
    add_project_arguments('-DDISABLE_BUILDTIME', language: 'cpp')
endif
if get_option('ENABLE_PROFILING') and ['linux', 'freebsd'].contains(host_machine.system())
    add_project_arguments('-pg', language: 'cpp')
    add_project_link_arguments('-pg', language: 'cpp')
endif
if get_option('ENABLE_TEST_SUITE')
    common_deps += subproject('gmock-1.7.0').get_variable('gmock_dep')
    common_deps += subproject('benchmark').get_variable('benchmark_dep')
endif
if get_option('ENABLE_LOCALECOMPARE')
    if not cc.cmd_array().contains('qt_sqlite_plugin')
        error('Locale-aware comparison in SQLite is only available with native SQLite 3, not through QT\'s SQLite plugin.')
    endif
endif

# Optionally target macOS app store
if get_option('TARGET_APPSTORE')
    add_project_arguments('-D__MACAPPSTORE__')
endif

# Build up the sources variable
src_mixxx = []

subdir('lib')
subdir('res')
subdir('src')

# Git stuff
git_branch = run_command(git_exe, 'rev-parse', '--abbrev-ref', 'HEAD').stdout().strip()
git_rev = run_command(git_exe, 'rev-parse', '--short', 'HEAD').stdout().strip()
message('Building @0@ - rev. @1@'.format(git_branch, git_rev))


# Override MIXXX VERSION define with meson project version
extra_cc_flags = [
    '-DMIXXX_VERSION="@0@"'.format(meson.project_version()),
    '-DSETTINGS_FILE="mixxx.cfg"'
]
# Set settings file per platform
if host_machine.system() == 'windows'
    extra_cc_flags += ['-DSETTINGS_PATH=".mixxx"']
endif

# Process Qt UI files
ui_processed = qt5_mod.preprocess(ui_files: src_ui_files)

# Generate build.h file
conf_build = configuration_data()
conf_build.set_quoted('BUILD_BRANCH', git_branch)
conf_build.set_quoted('BUILD_REV', git_rev)
build_h = configure_file(output: 'build.h', configuration: conf_build)


libmixxx = static_library('libmixxx', src_mixxx, build_h, ui_processed, gen_proto,
  dependencies: common_deps,
  include_directories: inc_project,
  cpp_args: extra_cc_flags
)

mixxx_main = executable('mixxx', ['src/main.cpp'], gen_proto,
    link_with: [libmixxx, mixxx_qrc],
    include_directories: inc_project,
    dependencies: common_deps,
    install:true
)

if get_option('ENABLE_TESTS')
    mixxx_test = executable('mixxx-tests', src_tests,
        include_directories: inc_project,
        link_with:[libmixxx, mixxx_qrc],
        dependencies:common_deps
    )
endif
