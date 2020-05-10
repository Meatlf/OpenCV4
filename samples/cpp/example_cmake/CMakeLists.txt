# cmake needs this line
cmake_minimum_required(VERSION 3.1)

# Define project name
project(opencv_example_project)

set(OpenCV_DIR "/usr/local/opencv430") 

# Find OpenCV, you may need to set OpenCV_DIR variable
# to the absolute path to the directory containing OpenCVConfig.cmake file
# via the command line or GUI
find_package(OpenCV 4.3 REQUIRED PATHS "/usr/local/opencv430/lib")

# If the package has been found, several variables will
# be set, you can find the full list with descriptions
# in the OpenCVConfig.cmake file.
# Print some message showing some of them
message(STATUS "OpenCV library status:")
message(STATUS "    config: ${OpenCV_DIR}")
message(STATUS "    version: ${OpenCV_VERSION}")
message(STATUS "    libraries: ${OpenCV_LIBS}")
message(STATUS "    include path: ${OpenCV_INCLUDE_DIRS}")

# Declare the executable target built from your sources
add_executable(opencv_example example.cpp)
add_executable(contours2 contours2.cpp)
add_executable(convexhull convexhull.cpp)

include_directories( ${OpenCV_INCLUDE_DIRS} "/usr/local/opencv430/include")

# Link your application with OpenCV libraries
target_link_libraries(opencv_example PRIVATE ${OpenCV_LIBS})
target_link_libraries(contours2 PRIVATE ${OpenCV_LIBS})
target_link_libraries(convexhull PRIVATE ${OpenCV_LIBS})