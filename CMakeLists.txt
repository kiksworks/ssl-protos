cmake_minimum_required(VERSION 2.8.8 FATAL_ERROR)

if(NOT Protobuf_FOUND)
  find_package(Protobuf 3.0.0 REQUIRED)
elseif(Protobuf_VERSION VERSION_LESS "3.0.0")
  message(FATAL_ERROR "Protobuf version must be at least 3.0.0!")
endif()

if(NOT EXISTS ${Protobuf_PROTOC_EXECUTABLE})
  message(FATAL_ERROR "Could not find Protobuf Compiler!")
endif()

include_directories(${Protobuf_INCLUDE_DIRS})

add_subdirectory(grsim)
add_subdirectory(refbox)
add_subdirectory(vision)

add_library(ssl-protos
  $<TARGET_OBJECTS:grsim>
  $<TARGET_OBJECTS:refbox>
  $<TARGET_OBJECTS:vision>
)
