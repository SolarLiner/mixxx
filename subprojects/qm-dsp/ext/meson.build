src_kiss = files([
    'kissfft/kiss_fft.c',
    'kissfft/kiss_fftr.c'
])

ext_lib = static_library(lib_modname_tpl.format('kissfft'), src_kiss, include_directories: inc, dependencies: deps)
deps += [declare_dependency(include_directories: inc, link_with: ext_lib)]
