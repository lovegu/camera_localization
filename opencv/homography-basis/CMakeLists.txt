project(homography-basis-visp)
cmake_minimum_required(VERSION 2.8)

find_package(OpenCV)

include_directories(${OpenCV_INCLUDE_DIRS})

set(tutorial_cpp
  homography-dlt-opencv.cpp
  pose-from-homography-dlt-opencv.cpp)

foreach(cpp ${tutorial_cpp})
  # Compute the name of the binary to create
  get_filename_component(binary ${cpp} NAME_WE)

  # From source compile the binary and add link rules
  add_executable(${binary} ${cpp})
  target_link_libraries(${binary} ${OpenCV_LIBRARIES})
endforeach()

