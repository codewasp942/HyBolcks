﻿cmake_minimum_required (VERSION 3.8)

project ("HyBolcks")

IF(CMAKE_CL_64)
    set(BUILD_PLATFORM x64)
ELSE(CMAKE_CL_64)
    set(BUILD_PLATFORM x86)
ENDIF(CMAKE_CL_64)

# copy FLTK headers and libs into your computer

aux_source_directory("./graphic" SRC_FILES)
aux_source_directory("./world" SRC_FILES)
include_directories("./include")

link_libraries(debug	fltkd.lib)
link_libraries(debug	fltkformsd.lib)
link_libraries(debug	fltkgld.lib)
link_libraries(debug	fltkimagesd.lib)
link_libraries(debug	fltkjpegd.lib)
link_libraries(debug	fltkpngd.lib)
link_libraries(debug	fltkzlibd.lib)

link_libraries(optimized	fltk.lib)
link_libraries(optimized	fltkforms.lib)
link_libraries(optimized	fltkgl.lib)
link_libraries(optimized	fltkimages.lib)
link_libraries(optimized	fltkjpeg.lib)
link_libraries(optimized	fltkpng.lib)
link_libraries(optimized	fltkzlib.lib)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/bin/${BUILD_PLATFORM}")

add_executable(HyBlocks main.cpp ${SRC_FILES})