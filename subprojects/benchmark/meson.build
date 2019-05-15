project('benchmark', 'cpp', version: '2.3.0-mixxx')

src = files([
    'src/benchmark.cc',
    'src/colorprint.cc',
    'src/commandlineflags.cc',
    'src/console_reporter.cc',
    'src/csv_reporter.cc',
    'src/json_reporter.cc',
    'src/log.cc',
    'src/reporter.cc',
    'src/re_posix.cc',
    'src/re_std.cc',
    'src/sleep.cc',
    'src/string_util.cc',
    'src/sysinfo.cc',
    'src/walltime.cc'
])

inc = include_directories('include')

lib = library('benchmark', src, include_directories: inc)

benchmark_dep = declare_dependency(include_directories: inc, link_with: lib)
