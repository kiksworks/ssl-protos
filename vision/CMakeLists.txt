file(GLOB_RECURSE PROTO_FILES *.proto)
protobuf_generate_cpp(PROTO_CC PROTO_H ${PROTO_FILES})
add_library(ssl-protos-vision ${PROTO_CC} ${PROTO_H})
