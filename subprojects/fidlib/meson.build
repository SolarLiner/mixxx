project('fidlib', 'c',
  version : '2.3.0-mixxx',
  default_options : ['warning_level=3'])

if host_machine.system() == 'linux'
  add_project_arguments('-DT_LINUX', language: 'c')
elif host_machine.system() == 'cygwin'
  add_project_arguments('-DT_MINGW', language: 'c')
elif meson.get_compiler('c').get_id() == 'msvc'
  add_project_arguments('DT_MSVC', language: 'c')
endif

src = ['fidlib.c']
inc = include_directories('.')
lib = library('fidlib', src, install: true)

fidlib_dep = declare_dependency(include_directories: inc, link_with: lib)
