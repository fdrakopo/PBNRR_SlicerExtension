cmake_minimum_required(VERSION 2.8.9)

project(PBNRR)

#-----------------------------------------------------------------------------
# Extension meta-information
set(EXTENSION_HOMEPAGE "http://www.slicer.org/slicerWiki/index.php/Documentation/Nightly/Extensions/PBNRR")
set(EXTENSION_CATEGORY "Registration")
set(EXTENSION_CONTRIBUTORS "Fotis Drakopoulos (CRTC), Yixun Liu (CRTC), Andriy Kot (CRTC), Andrey Fedorov (SPL B&W Harvard), Olivier Clatz (Asclepios INRIA) and Nikos Chrisochoides (CRTC)")
set(EXTENSION_DESCRIPTION "This extension integrates an ITK implementation of a Physics-Based Non-Rigid Registration (PBNRR) method. The PBNRR compensates for the brain shift during the Image-Guided Neurosurgery (IGNS). The method uses a linear homogeneous bio-mechanical model to compute a dense deformation field that defines a transformation for every point in the fixed image to the moving image. The PBNRR consists of three components (Feature Point Selection, Block Matching and Finite Element Solver) combine together to provide a user-friendly interface.")
set(EXTENSION_ICONURL "http://www.slicer.org/slicerWiki/images/e/ef/CRTC_logo.jpg")
set(EXTENSION_SCREENSHOTURLS "http://www.slicer.org/slicerWiki/images/6/63/Case1_input.png  http://www.slicer.org/slicerWiki/images/a/a4/Case1_output.png http://www.slicer.org/slicerWiki/images/d/db/PBNRR_panel.png")


#-----------------------------------------------------------------------------
# Extension dependencies
find_package(Slicer REQUIRED)
include(${Slicer_USE_FILE})

#-----------------------------------------------------------------------------
# Extension modules
add_subdirectory(PBNRR)

#-----------------------------------------------------------------------------
include(${Slicer_EXTENSION_CPACK})
