if not FEATURE_BULK
    subdir_done()
endif

src_mixxx += files([
    './bulkcontroller.cpp',
    './bulkenumerator.cpp'
])

if not FEATURE_HID
    src_mixxx += files('../hid/hidcontrollerpresetfilehandler.cpp')
endif
