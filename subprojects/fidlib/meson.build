project('fidlib', 'c',
  version : '2.3.0-mixxx',
  default_options : ['warning_level=3'])

cc = meson.get_compiler('c')

m_dep = cc.find_library('m')

if host_machine.system() == 'linux'
  add_project_arguments('-DT_LINUX', language: 'c')
elif host_machine.system() == 'cygwin'
  add_project_arguments('-DT_MINGW', language: 'c')
elif cc.get_id() == 'msvc'
  add_project_arguments('DT_MSVC', language: 'c')
endif

src = ['fidlib.c']
inc = include_directories('.')
lib = library('fidlib', src, dependencies: m_dep, install: true)

fidlib_dep = declare_dependency(include_directories: inc, link_with: lib)
