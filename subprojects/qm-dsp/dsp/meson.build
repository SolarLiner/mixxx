src_dsp = []

# Those contains code needed for the other DSP

subdir('chromagram')
subdir('keydetection')
# subdir('mfcc')
subdir('onsets')
subdir('phasevocoder')
subdir('rateconversion')
# subdir('rhythm')
# subdir('segmentation')
subdir('signalconditioning')
subdir('tempotracking')
subdir('tonal')
subdir('transforms')
# subdir('wavelet')

dsp_lib = static_library(lib_modname_tpl.format('dsp'),
    src_dsp,
    dependencies: deps
)
