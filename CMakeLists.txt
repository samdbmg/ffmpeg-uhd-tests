cmake_minimum_required(VERSION 2.6)
project(ffmpeg-uhd-tests)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "-D__STDC_CONSTANT_MACROS")
list(APPEND CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR})

find_package(FFmpeg COMPONENTS AVCODEC AVFORMAT AVUTIL REQUIRED) #add here the list of ffmpeg components required

find_path(AVCODEC_INCLUDE_DIR libavcodec/avcodec.h)
find_library(AVCODEC_LIBRARY avcodec)

find_path(AVFORMAT_INCLUDE_DIR libavformat/avformat.h)
find_library(AVFORMAT_LIBRARY avformat)

find_path(AVUTIL_INCLUDE_DIR libavutil/avutil.h)
find_library(AVUTIL_LIBRARY avutil)

find_path(SWSCALE_INCLUDE_DIR libswscale/swscale.h)
find_library(SWSCALE_LIBRARY swscale)

add_executable(ffmpeg-uhd-tests muxing.c)
target_include_directories(ffmpeg-uhd-tests PRIVATE ${AVCODEC_INCLUDE_DIR} ${AVFORMAT_INCLUDE_DIR} ${AVUTIL_INCLUDE_DIR} ${SWSCALE_INCLUDE_DIR})
target_link_libraries(ffmpeg-uhd-tests PRIVATE ${SWSCALE_LIBRARY} ${AVCODEC_LIBRARY} ${AVFORMAT_LIBRARY} ${AVUTIL_LIBRARY} m)