file(GLOB_RECURSE PROTO_FILES *.proto)
protobuf_generate_cpp(PROTO_CC PROTO_H ${PROTO_FILES})
add_library(refbox OBJECT ${PROTO_CC} ${PROTO_H})
target_link_libraries(refbox protobuf::libprotobuf)
