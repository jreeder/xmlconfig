#CMake file for xmlconfig

project(XMLCONFIG)

cmake_minimum_required(VERSION 2.8)

file(GLOB tinyxml src/tinyxml/*.cpp)
file(GLOB xmlconfig src/xmlconfig/*cpp)

source_group("tinyxml" FILES ${tinyxml})
source_group("xmlconfig" FILES ${xmlconfig})

file(GLOB header_tinyxml include/tinyxml/*.h)
file(GLOB header_xmlconfig include/xmlconfig/*.h)

source_group("tinyxml" FILES ${header_tinyxml})
source_group("xmlconfig" FILES ${header_xmlconfig})

include_directories("include")

add_library(xmlconfig ${tinyxml} ${xmlconfig} ${header_xmlconfig} ${header_tinyxml})

set_target_properties(xmlconfig PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/lib)

install(TARGETS xmlconfig DESTINATION lib)
install(FILES ${header_xmlconfig} DESTINATION include)