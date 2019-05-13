project('qtscript-bytearray', 'cpp',
  version : '2.3.0-mixxx',
  default_options : ['warning_level=3', 'cpp_std=c++11'])

qt5_mod = import('qt5')
qt5_dep = dependency('qt5', modules: ['Core', 'Script'])

inc = include_directories('.')

src_processed = qt5_mod.preprocess(
  moc_headers: ['bytearrayclass.h', 'bytearrayprototype.h'],
  moc_sources: ['bytearrayclass.cpp', 'bytearrayprototype.cpp'])

lib = library('qtscript-bytearray', src_processed,
           dependencies: qt5_dep,
           install : true)

qtscript_bytearray_dep = declare_dependency(include_directories: inc, link_with: lib)
