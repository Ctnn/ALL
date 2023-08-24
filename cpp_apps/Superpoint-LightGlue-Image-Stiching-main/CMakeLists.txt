cmake_minimum_required(VERSION 3.10)
project(FeatureMatcherDemo)

# Set C++ standard
set(CMAKE_CXX_STANDARD 11)

# ���ñ�������
set(CMAKE_BUILD_TYPE Release)

# Find OpenCV
#set(OpenCV_INCLUDE_DIRS "./opencv/include")
#set(OpenCV_LIBS "../opencv/lib/opencv_world455")
#set(OpenCV_INCLUDE_DIRS "/home/firefly/opencv/opencv_build/opencv/include")
find_package(OpenCV REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})


# ���ӿ�ִ���ļ�������Ĳ���·��
add_library(feature_matcher SHARED common.h superpoint.h superpoint.cpp  lightglue.h lightglue.cpp)
target_include_directories(feature_matcher PRIVATE ${OpenCV_INCLUDE_DIRS} )
target_link_libraries(feature_matcher ${OpenCV_LIBS} )
target_compile_definitions(feature_matcher PRIVATE FEATURE_MATCHER_EXPORTS)

# ��������cppDemo��ִ���ļ�
add_executable(cppDemo common.h cppDemo.cpp)
target_include_directories(cppDemo PRIVATE ${OpenCV_INCLUDE_DIRS} )
target_link_libraries(cppDemo
                      ${OpenCV_LIBS}
                      feature_matcher)

