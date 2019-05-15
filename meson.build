project('mixxx', 'c', 'cpp', version: '2.3.0a-pre', default_options:['cpp_std=c++11'])

# Utils
git_exe = find_program('git')

# Modules
qt5_mod = import('qt5')

# Dependencies
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
libusb_dep = dependency('libusb-1.0')
libmodplug_dep = dependency('libmodplug')
lilv_dep = dependency('lilv-0', required: get_option('FEATURE_LV2'))
portaudio_dep = dependency('portaudio-2.0')
wavpack_dep = dependency('wavpack')

# Subprojects
fidlib_dep = subproject('fidlib').get_variable('fidlib_dep')
gtest_dep = subproject('gtest-1.7.0').get_variable('gtest_mainless_dep')
pa_ringbuf_dep = subproject('pa-ringbuffer').get_variable('pa_ringbuffer_dep')
libebur128_dep = subproject('libebur128').get_variable('ebur128_dep')
qm_dsp_dep = subproject('qm-dsp').get_variable('qm_dsp_dep')
qtscript_bytearray_dep = subproject('qtscript-bytearray').get_variable('qtscript_bytearray_dep')
replaygain_dep = subproject('replaygain').get_variable('replaygain_dep')
soundtouch_dep = subproject('soundtouch').get_variable('soundtouch_dep')
xwax_dep = subproject('xwax').get_variable('xwax_dep')

common_deps = [
    threads_dep,
    opus_dep,
    qt5_dep,
    libusb_dep,
    libmodplug_dep,
    lilv_dep,
    portaudio_dep,
    wavpack_dep,
    fidlib_dep,
    gtest_dep,
    pa_ringbuf_dep,
    libebur128_dep,
    qm_dsp_dep,
    qtscript_bytearray_dep,
    replaygain_dep,
    soundtouch_dep,
    xwax_dep
]

# includes
inc_project = include_directories('src', 'lib')

# Optional features
if get_option('ENABLE_HID')
    hid_dep = dependency('hidapi-libusb', fallback: ['hidapi-0.8.0-rc1', 'hidapi_dep'])
    common_deps += hid_dep
    add_project_arguments('-D__HID__', language: 'cpp')
endif
if get_option('FEATURE_MP4')
    libmp4_dep = dependency('mp4v2', required: false) # Disable mp4, libmp4 dependency not found on Ubuntu Disco
    if not libmp4_dep.found()
        libmp4_dep = dependency('mp4')
    endif
    common_deps += libmp4_dep
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
    '-DMIXXX_VERSION=@0@'.format(meson.project_version())
]

ui_processed = qt5_mod.preprocess(ui_files: src_ui_files)

libmixxx = static_library('libmixxx', src_mixxx, ui_processed, gen_proto,
  dependencies: common_deps,
  include_directories: inc_project,
  cpp_args: extra_cc_flags
)

mixxx_main = executable('mixxx', ['src/main.cpp'], gen_proto,
    link_with: [libmixxx, mixxx_qrc],
    include_directories: inc_project,
    dependencies: [qt5_dep],
    install:true
)

if get_option('ENABLE_TESTS')
    mixxx_test = executable('mixxx-tests', src_tests, link_with:[libmixxx_static, mixxx_qrc], dependencies:[qt5_dep])
endif
