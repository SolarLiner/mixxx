project('gmock', 'cpp', version: '2.3.0-mixxx')

gtest_dep = subproject('gtest-1.7.0').get_variable('gtest_mainless_dep')

src = files(['src/gmock-all.cc', 'src/gmock-cardinalities.cc', 'src/gmock-internal-utils.cc', 'src/gmock-matchers.cc', 'src/gmock-spec-builders.cc', 'src/gmock.cc'])
src_wmain = src + files('src/gmock_main.cc')

inc = include_directories('include')

lib = library('gmock', src, dependencies: gtest_dep, include_directories: inc)

gmock_dep = declare_dependency(include_directories:inc, link_with: lib)
