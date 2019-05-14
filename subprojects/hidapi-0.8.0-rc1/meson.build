project('hidapi', 'c', version: '0.8.0-rc1')

threads_dep = dependency('threads')
libudev_dep = dependency('libudev')
rt_dep = meson.get_compiler('c').find_library('rt')
libusb_dep = dependency('libusb-1.0', required: false)
setupapi_dep = meson.get_compiler('c').find_library('setupapi', required: false)

inc = include_directories('hidapi')

if host_machine.system() == 'windows'
    if not setupapi_dep.found()
        error('Windows builds need setupapi')
    endif
    src = ['windows/hid.c']
elif host_machine.system() == 'linux'
    if not libusb_dep.found()
        error('Linux builds need libusb')
    endif
    src = ['libusb/hid.c']
else
    src = ['mac/hid.c']
endif

lib = library('libhidapi', src, include_directories: inc, dependencies: [
    threads_dep,
    libusb_dep,
    libudev_dep,
    rt_dep
])

hidapi_dep = declare_dependency(include_directories: inc, link_with: lib)
