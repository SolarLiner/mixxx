project('replaygain', 'cpp',
  version : '2.3.0-mixxx',
  default_options : ['warning_level=3', 'cpp_std=c++14'])

inc = include_directories('.')

lib = library('replaygain',
  'replaygain.cpp',
  install : true
)

replaygain_dep = declare_dependency(include_directories: inc, link_with: lib)
