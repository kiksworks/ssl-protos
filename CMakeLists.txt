cmake_minimum_required(VERSION 3.9 FATAL_ERROR)
project(ssl-protos CXX)

if(NOT Protobuf_FOUND)
  find_package(Protobuf REQUIRED)
endif()

if(NOT EXISTS ${Protobuf_PROTOC_EXECUTABLE})
  message(FATAL_ERROR "Could not find Protobuf Compiler!")
endif()

add_subdirectory(ssl-protos/grsim)
add_subdirectory(ssl-protos/refbox)
add_subdirectory(ssl-protos/vision)

add_library(ssl-protos
  $<TARGET_OBJECTS:grsim>
  $<TARGET_OBJECTS:refbox>
  $<TARGET_OBJECTS:vision>
)
target_link_libraries(ssl-protos
  PRIVATE   protobuf::libprotobuf
  INTERFACE protobuf::libprotobuf
)
target_include_directories(ssl-protos SYSTEM
  INTERFACE ${CMAKE_CURRENT_BINARY_DIR}
)
add_library(ssl-protos::ssl-protos ALIAS ssl-protos)
