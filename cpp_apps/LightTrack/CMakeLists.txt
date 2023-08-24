cmake_minimum_required(VERSION 3.16)


project( LightTrack )
find_package( OpenCV REQUIRED )
include_directories( ${OpenCV_INCLUDE_DIRS} )
add_executable(LightTrack
   src/main.cpp
   src/LightTrack.cpp
   )


set(
   include_libs
   ${PROJECT_SOURCE_DIR}/include
)

include_directories(${include_libs})


target_link_libraries( LightTrack ${OpenCV_LIBS} ${PROJECT_SOURCE_DIR}/3rdparty/librknn_api/aarch64/librknn_api.so )

