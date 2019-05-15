
if host_machine.system() == 'windows'
    cpp_args = ['-D_WIN32']
else
    if not threads_dep.found()
        error('Linux needs Threads dependency')
    endif
    cpp_args = ['-DUSE_PTHREADS']
endif

thread_lib = static_library(lib_modname_tpl.format('thread'), 'Thread.cpp', include_directories: inc, dependencies: threads_dep, cpp_args: cpp_args)
