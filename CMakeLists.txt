cmake_minimum_required(VERSION 2.8.8 FATAL_ERROR)

if(NOT Protobuf_FOUND)
  find_package(Protobuf REQUIRED)
  include_directories(${PROTOBUF_INCLUDE_DIRS})
endif()

if(NOT EXISTS ${PROTOBUF_PROTOC_EXECUTABLE})
  message(FATAL_ERROR "Could not find Protobuf Compiler!")
endif()

add_subdirectory(grsim)
add_subdirectory(refbox)
add_subdirectory(vision)

add_library(ssl-protos
  $<TARGET_OBJECTS:grsim>
  $<TARGET_OBJECTS:refbox>
  $<TARGET_OBJECTS:vision>
)
