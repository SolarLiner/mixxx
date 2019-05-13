project('mixxx', 'c', 'cpp', version: '2.3.0a-pre')

# Utils
git_exe = find_program('git')

# Modules
qt5_mod = import('qt5')

# Dependencies
threads_dep = dependency('threads', required: false)
qt5_dep = dependency('qt5', modules: ['Core', 'Concurrent', 'Gui', 'Sql', 'Widgets', 'Xml'])
protobuf_dep = dependency('protobuf')

# Subprojects

gtest_dep = subproject('gtest').get_variable('gtest_main_less_dep')

common_deps = [
    threads_dep,
    qt5_dep,
    gtest_dep
]

# includes
inc_project = include_directories('src', 'lib')

# Build up the sources variable
subdir('res')
subdir('src')

# Git stuff
git_branch = run_command(git_exe, 'rev-parse', '--abbrev-ref', 'HEAD').stdout().strip()
git_rev = run_command(git_exe, 'rev-parse', '--short', 'HEAD').stdout().strip()
message('Building @0@ - rev. @1@'.format(git_branch, git_rev))

# Build Mixxx (libmixxx is defined in src/meson.build)
mixxx_main = executable('mixxx', ['src/main.cpp'], link_with: [libmixxx_static, mixxx_qrc], dependencies: [qt5_dep], install:true)

if get_option('ENABLE_TESTS')
    mixxx_test = executable('mixxx-tests', src_tests, link_with:[libmixxx_static, mixxx_qrc], dependencies:[qt5_dep])
endif
