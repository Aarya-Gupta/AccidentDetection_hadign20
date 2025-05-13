cmake_minimum_required(VERSION 3.0...3.5)
project(VA)

set(OpenCV_DIR "C:/OpenCV/opencv/build/x64/vc16")
find_package(OpenCV REQUIRED)

# Check if OpenCV was found
if(OpenCV_FOUND)
    message(STATUS "OpenCV version: ${OpenCV_VERSION}")
else()
    message(FATAL_ERROR "OpenCV not found")
endif() 

include_directories(C:/OpenCV/opencv/build/include)

include_directories( "include/")

add_executable(VA main.cpp detector.cpp HungarianAlg.cpp 
Kalman.cpp Multitracker.cpp yolo_utils.cpp Track.cpp Display.cpp SpeedEstimator.cpp
Intersection.cpp MultiCams.cpp)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(ONNXRUNTIME_ROOT_PATH C:/onnxruntime-win-x64-1.19.0)
set(ONNXRUNTIME_INCLUDE_DIRS C:/onnxruntime-win-x64-1.19.0/include/onnxruntime
                             C:/onnxruntime-win-x64-1.19.0/onnxruntime
                             C:/onnxruntime-win-x64-1.19.0/include/onnxruntime/core/session/)
set(ONNXRUNTIME_LIB C:/onnxruntime-win-x64-1.19.0/lib/onnxruntime.dll)
include_directories(C:/onnxruntime-win-x64-1.19.0/include)  
target_link_libraries(VA "C:/onnxruntime-win-x64-1.19.0/lib/onnxruntime.dll")
 
target_compile_features(VA PRIVATE cxx_std_14)
target_link_libraries(VA "C:/OpenCV/opencv/build/bin/opencv_videoio_ffmpeg4100_64.dll") 

