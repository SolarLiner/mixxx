project('soundtouch', 'cpp',
  version : '2.1.1',
  default_options : ['warning_level=3', 'cpp_std=c++14'])

lib = library('soundtouch',
           'InterpolateShannon.cpp',
           'cpu_detect_x86.cpp',
           'InterpolateLinear.cpp',
           'FIFOSampleBuffer.cpp',
           'InterpolateCubic.cpp',
           'mmx_optimized.cpp',
           'FIRFilter.cpp',
           'PeakFinder.cpp',
           'TDStretch.cpp',
           'sse_optimized.cpp',
           'AAFilter.cpp',
           'RateTransposer.cpp',
           'BPMDetect.cpp',
           'SoundTouch.cpp',
           install : true)
inc = include_directories('.')

soundtouch_dep = declare_dependency(include_directories: inc, link_with: lib)
