project(bst_image_proto)

file(GLOB RAW_PROTO_SRCS  *.proto)
message(STATUS "bst_image_proto PROTOBUF_IMPORT_DIRS = ${PROTOBUF_IMPORT_DIRS}")
PROTOBUF_GENERATE_CPP(PROTO_SRCS PROTO_HDRS ${RAW_PROTO_SRCS})
add_library(bst_image_proto SHARED ${PROTO_SRCS} ${PROTO_HDRS})

message(${BST_LIB_INSTALL_PATH})

install(TARGETS bst_image_proto LIBRARY DESTINATION ${BST_LIB_INSTALL_PATH})
