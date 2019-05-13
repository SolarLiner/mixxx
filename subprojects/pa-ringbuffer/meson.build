project('pa-ringbuffer', 'c', version: '2.3.0-mixxx')

inc = include_directories('.')
src = files('./pa_ringbuffer.c')

lib = library('libpa-ringbuffer', src)

pa_ringbuffer_dep = declare_dependency(include_directories: inc, link_with: lib)
