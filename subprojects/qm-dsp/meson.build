project('qm-dsp', 'c', 'cpp', version: '2.3.0-mixxx', default_options: ['cpp_std=c++11'])
cc = meson.get_compiler('c')

lib_name = 'lib@0@'.format(meson.project_name())
lib_modname_tpl = lib_name+'-@0@'

m_dep = cc.find_library('m')
threads_dep = dependency('threads', required: false)

deps = [m_dep, threads_dep]

inc = include_directories('.', 'include')

if host_machine.system() == 'windows'
    add_project_arguments('-D_WIN32', language: 'cpp')
endif

if threads_dep.found()
    add_project_arguments('-DUSE_PTHREADS', language: 'cpp')
endif

# Avoid double to float conversion errors
add_project_arguments('-Dkiss_fft_scalar=double', language:'cpp')

# Build code that is needed for the library first, it adds itself as a dependency
subdir('base')
subdir('maths')
subdir('ext')

subdir('thread')
# Don't build hmm, needs Fortran BLAM and LAPACK libraries
#subdir('hmm')
subdir('dsp')

dsp_libs = [
    base_lib,
    thread_lib,
    ext_lib,
    # hmm_lib,
    maths_lib,
    dsp_lib
]

qm_dsp_dep = declare_dependency(include_directories: inc, link_with: dsp_libs)
