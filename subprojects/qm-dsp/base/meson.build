src_base = files([
    # './KaiserWindow.cpp',
    './Pitch.cpp',
    # './SincWindow.cpp'
])

base_lib = static_library(lib_modname_tpl.format('base'), src_base, dependencies: deps, include_directories:inc)
deps += [declare_dependency(include_directories: inc, link_with: base_lib)]
