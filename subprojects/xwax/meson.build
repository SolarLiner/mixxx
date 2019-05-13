project('xwax',
  version : '2.3.0-mixxx',
  default_options : ['warning_level=3', 'cpp_std=c++14'])

qtscript_bytearray_dep = subproject('qtscript-bytearray').get_variable('qtscript_bytearray_dep')

if host_machine.system() == 'windows'
  add_languages('cpp')
  src = ['./timecoder_win32.cpp', './lut_win32.cpp']
else
  add_languages('c')
  src = ['./lut.c', './timecoder.c']
endif

inc = include_directories('.')

lib = library('xwax', src, install : true, dependencies: qtscript_bytearray_dep)

xwax_dep = declare_dependency(include_directories: inc, link_with: lib)
