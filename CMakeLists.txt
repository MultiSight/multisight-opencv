cmake_minimum_required(VERSION 2.8)
project(opencv)

include(common.cmake NO_POLICY_SCOPE)

include(ExternalProject)

ExternalProject_Add(opencv
  URL ${CMAKE_CURRENT_SOURCE_DIR}/opencv-2.4.9.zip
  PREFIX ${CMAKE_CURRENT_BINARY_DIR}/artifacts
  INSTALL_DIR ${CMAKE_CURRENT_BINARY_DIR}/artifacts
  CMAKE_ARGS
    -DCMAKE_INSTALL_PREFIX=${CMAKE_CURRENT_BINARY_DIR}/artifacts
    -DBUILD_opencv_calib3d=OFF
    -DBUILD_opencv_contrib=OFF
    -DBUILD_opencv_dynamicuda=OFF
    -DBUILD_opencv_features2d=OFF
    -DBUILD_opencv_flann=OFF
    -DBUILD_opencv_gpu=OFF
    -DBUILD_opencv_highgui=OFF
    -DBUILD_opencv_legacy=OFF
    -DBUILD_opencv_ml=OFF
    -DBUILD_opencv_nonfree=OFF
    -DBUILD_opencv_objdetect=OFF
    -DBUILD_opencv_ocl=OFF
    -DBUILD_opencv_photo=OFF
    -DBUILD_opencv_stitching=OFF
    -DBUILD_opencv_superres=OFF
    -DBUILD_opencv_ts=OFF
    -DBUILD_opencv_video=OFF
    -DBUILD_opencv_videostab=OFF
    -DBUILD_opencv_viz=OFF
    -DBUILD_opencv_world=OFF
)

SET(CMAKE_INSTALL_PREFIX ${devel_artifacts_path})

install(DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/artifacts/include/opencv DESTINATION include)
install(DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/artifacts/include/opencv2 DESTINATION include)
install(DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/artifacts/lib/ DESTINATION lib FILES_MATCHING PATTERN "libopencv_core.*")
install(DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/artifacts/lib/ DESTINATION lib FILES_MATCHING PATTERN "libopencv_imgproc.*")
