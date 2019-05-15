src_pca = files('pca/pca.c')

src_maths = files([
    './Correlation.cpp',
    './CosineDistance.cpp',
    './KLDivergence.cpp',
    './MathUtilities.cpp',
])

maths_lib = static_library(lib_modname_tpl.format('base'), src_pca, src_maths, dependencies: deps, include_directories: inc)
deps += [declare_dependency(include_directories: inc, link_with: maths_lib)]
