
#-----------------------------------------------------------------------------
set(BASELINE ${CMAKE_CURRENT_SOURCE_DIR}/../../Data/Baseline)
set(INPUT ${CMAKE_CURRENT_SOURCE_DIR}/../../Data/Input)
set(TEMP "${CMAKE_BINARY_DIR}/Testing/Temporary")

set(CLP ${MODULE_NAME})

#-----------------------------------------------------------------------------
add_executable(${CLP}Test ${CLP}Test.cxx)
target_link_libraries(${CLP}Test ${CLP}Lib)
set_target_properties(${CLP}Test PROPERTIES LABELS ${CLP})

#-----------------------------------------------------------------------------
set(testname ${CLP}Test1)
add_test(NAME ${testname} COMMAND ${SEM_LAUNCH_COMMAND} $<TARGET_FILE:${CLP}Test>
  ModuleEntryPoint
  --movingImage             ${BASELINE}/case1/MovingImage.nii.gz 
  --fixedImage              ${BASELINE}/case1/FixedImage.nii.gz
  --maskImage               ${BASELINE}/case1/MovingMask.nii.gz
  --mesh                    ${BASELINE}/case1/Mesh.vtk
  --poissonRatio            0.45
  --youngModulus            0.0021
  --interpolationSteps      5
  --outlierRejectionSteps   2   
  --rejectionFraction       0.25
  --selectionFraction       0.05
  --windowRadius            4,4,1
  --blockRadius             1,1,1   
  --outputImage             warpedImage.nii.gz
   )
set_property(TEST ${testname} PROPERTY LABELS ${CLP})

set(testname ${CLP}Test2)
add_test(NAME ${testname} COMMAND ${SEM_LAUNCH_COMMAND} $<TARGET_FILE:${CLP}Test>
  ModuleEntryPoint
  --movingImage             ${BASELINE}/case2/MovingImage.nii.gz 
  --fixedImage              ${BASELINE}/case2/FixedImage.nii.gz
  --maskImage               ${BASELINE}/case2/MovingMask.nii.gz
  --mesh                    ${BASELINE}/case2/Mesh.vtk
  --poissonRatio            0.45
  --youngModulus            0.0021
  --interpolationSteps      5
  --outlierRejectionSteps   3   
  --rejectionFraction       0.25
  --selectionFraction       0.05
  --windowRadius            3,3,1
  --blockRadius             1,1,1   
  --outputImage             warpedImage.nii.gz
   )
set_property(TEST ${testname} PROPERTY LABELS ${CLP})

#-----------------------------------------------------------------------------
#ExternalData_add_target(${CLP}Data)
