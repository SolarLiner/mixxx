if not get_option('FEATURE_BULK')
    subdir_done()
endif

src_mixxx += files([
    './bulkcontroller.cpp',
    './bulkenumerator.cpp'
])

if not get_option('FEATURE_HID')
    src_mixxx += files('../hid/hidcontrollerpresetfilehandler.cpp')
endif
