project('qtscript-bytearray', 'cpp',
  version : '2.3.0-mixxx',
  default_options : ['warning_level=3', 'cpp_std=c++14'])

qt5_dep = dependency('qt5', modules: ['Core', 'Script'])

inc = include_directories('.')

lib = library('qtscript-bytearray',
           'bytearrayclass.cpp',
           'bytearrayprototype.cpp',
           dependencies: qt5_dep,
           install : true)

qtscript_bytearray_dep = declare_dependency(include_directories: inc, link_with: lib)
