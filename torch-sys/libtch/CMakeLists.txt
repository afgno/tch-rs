cmake_minimum_required(VERSION 3.5 FATAL_ERROR)
project(tch)

find_package(Torch REQUIRED)
find_package(TorchVision REQUIRED)

add_library(tch STATIC torch_api.cpp)
target_link_libraries(tch "${TORCH_LIBRARIES}")
target_link_libraries(tch TorchVision::TorchVision "-Wl,--whole-archive")
set_property(TARGET tch PROPERTY CXX_STANDARD 11)
install(TARGETS tch DESTINATION .)
