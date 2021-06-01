# CMakeList.txt: MyVedioPlayer 的 CMake 项目，在此处包括源代码并定义
# 项目特定的逻辑。
#
cmake_minimum_required (VERSION 3.8)

project ("MyVedioPlayer")


# 将源代码添加到此项目的可执行文件。
add_executable (MyVedioPlayer MyVedioPlayer.cpp MyVedioPlayer.h)




# ffmpeg


#ADD_DEFINITIONS(-D__STDC_LIMIT_MACROS -D_WEBSOCKETPP_CPP11_STL_ -DASIO_STANDALONE -D__STDC_FORMAT_MACROS)
####################################################
#  FFmpeg lib setting
####################################################

find_path(AVCODEC_INCLUDE_DIR libavcodec/avcodec.h)
find_library(AVCODEC_LIBRARY "avcodec")

find_path(AVFORMAT_INCLUDE_DIR libavformat/avformat.h)
find_library(AVFORMAT_LIBRARY "avformat")

find_path(AVUTIL_INCLUDE_DIR libavutil/imgutils.h)
find_library(AVUTIL_LIBRARY "avutil")

find_path(SWSCALE_INCLUDE_DIR libswscale/swscale.h)
find_library(SWSCALE_LIBRARY "swscale")

find_path(SDL_INCLUDE_DIR SDL2/SDL.h)
find_library(SDL_LIBRARY "SDL")



message(AVCODEC_INCLUDE_DIR ===== ${AVCODEC_INCLUDE_DIR})
message(JAVFORMAT_INCLUDE_DIR ===== ${AVFORMAT_INCLUDE_DIR})
message(AVUTIL_INCLUDE_DIR ===== ${AVUTIL_INCLUDE_DIR})
message(AVCODEC_LIBRARY ===== ${AVCODEC_LIBRARY})
message(AVFORMAT_LIBRARY ===== ${AVFORMAT_LIBRARY})
message(AVUTIL_LIBRARY ===== ${AVUTIL_LIBRARY})
message(SWSCALE_LIBRARY ===== ${SWSCALE_LIBRARY})
message(SDL_LIBRARY ===== ${SDL_LIBRARY})


target_include_directories( MyVedioPlayer
    PRIVATE
    ${AVCODEC_INCLUDE_DIR}
    ${AVFORMAT_INCLUDE_DIR}
    ${AVUTIL_INCLUDE_DIR}
    ${SWSCALE_INCLUDE_DIR}
    ${SDL_INCLUDE_DIR}
)

target_link_libraries( MyVedioPlayer
    PRIVATE
        ${AVCODEC_LIBRARY}
        ${AVFORMAT_LIBRARY}
        ${AVUTIL_LIBRARY}
        ${SWSCALE_LIBRARY}
        ${SDL_LIBRARY}
)
