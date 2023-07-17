cmake_minimum_required(VERSION 3.12 FATAL_ERROR)
project(ssl-protos CXX)

set(CMAKE_CXX_EXTENSIONS  OFF)
set(CMAKE_CXX_STANDARD    17)
set(CXX_STANDARD_REQUIRED ON)

if(NOT Protobuf_FOUND)
  find_package(Protobuf REQUIRED)
endif()

if(NOT TARGET protobuf::protoc)
  message(FATAL_ERROR "Could not find Protobuf Compiler!")
endif()

add_subdirectory(ssl-protos)

add_library(ssl-protos
  $<TARGET_OBJECTS:ssl-protos-obj>
)
target_link_libraries(ssl-protos
  PRIVATE   protobuf::libprotobuf
  INTERFACE protobuf::libprotobuf
)
target_include_directories(ssl-protos SYSTEM
  INTERFACE ${CMAKE_CURRENT_BINARY_DIR}
)
add_library(ssl-protos::ssl-protos ALIAS ssl-protos)
