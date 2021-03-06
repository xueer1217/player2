cmake_minimum_required(VERSION 3.15)
project(player)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS "-D__STDC_CONSTANT_MACROS")

############################
#设置搜索路径
###########################
set(CMAKE_INCLUDE_PATH
        "/usr/local/Cellar/ffmpeg/4.2.1_1/include"
        "/usr/local/Cellar/sdl2/2.0.10/include"
        )
set(CMAKE_LIBRARY_PATH
        "/usr/local/Cellar/ffmpeg/4.2.1_1/lib"
        "/usr/local/Cellar/sdl2/2.0.10/lib"
        )


find_path(AVCODEC_INCLUDE_DIR libavcodec/avcodec.h)
find_library(AVCODEC_LIBRARY avcodec)

find_path(AVFORMAT_INCLUDE_DIR libavformat/avformat.h)
find_library(AVFORMAT_LIBRARY avformat)

find_path(AVUTIL_INCLUDE_DIR libavutil/avutil.h)
find_library(AVUTIL_LIBRARY avutil)

find_path(AVDEVICE_INCLUDE_DIR libavdevice/avdevice.h)
find_library(AVDEVICE_LIBRARY avdevice)

find_path(AVFILTER_INCLUDE_DIR libavfilter/avfilter.h)
find_library(AVFILTER_LIBRARY avfilter)

find_path(POSTPROC_INCLUDE_DIR libpostproc/postprocess.h)
find_library(POSTPROC_LIBRARY postproc)

find_path(SWRESAMPLE_INCLUDE_DIR libswresample/swresample.h)
find_library(SWRESAMPLE_LIBRARY swresample)

find_path(SWSCALE_INCLUDE_DIR libswscale/swscale.h)
find_library(SWSCALE_LIBRARY swscale)

find_path(SDL_INCLUDE_DIR SDL2/SDL.h)
find_library(SDL_LIBRARY SDL2)

message("FFMPEG INFORMATION")
message("--------------------")
message(AVCODEC_INCLUDE_DIR=${AVCODEC_INCLUDE_DIR})
message(AVCODEC_LIBRARY=${AVCODEC_LIBRARY})
message("--------------------")
message(AVFORMAT_INCLUDE_DIR=${AVFORMAT_INCLUDE_DIR})
message(AVFORMAT_LIBRARY=${AVFORMAT_LIBRARY})
message("--------------------")
message(AVUTIL_INCLUDE_DIR=${AVUTIL_INCLUDE_DIR})
message(AVUTIL_LIBRARY=${AVUTIL_LIBRARY})
message("--------------------")
message(AVDEVICE_INCLUDE_DIR=${AVDEVICE_INCLUDE_DIR})
message(AVDEVICE_LIBRARY=${AVDEVICE_LIBRARY})
message("--------------------")
message(AVFILTER_INCLUDE_DIR=${AVFILTER_INCLUDE_DIR})
message(AVFILTER_LIBRARY=${AVFILTER_LIBRARY})
message("--------------------")
message(POSTPROC_INCLUDE_DIR=${POSTPROC_INCLUDE_DIR})
message(POSTPROC_LIBRARY=${POSTPROC_LIBRARY})
message("--------------------")
message(SWRESAMPLE_INCLUDE_DIR=${SWRESAMPLE_INCLUDE_DIR})
message(SWRESAMPLE_LIBRARY=${SWRESAMPLE_LIBRARY})
message("--------------------")
message(SWSCALE_INCLUDE_DIR=${SWSCALE_INCLUDE_DIR})
message(SWSCALE_LIBRARY=${SWSCALE_LIBRARY})
message("--------------------")
message(SDL_INCLUDE_DIR=${SDL_INCLUDE_DIR})
message(SDL_LIBRARY=${SDL_LIBRARY})


#video_play 仅播放画面
#audio_play 仅播放声音
#avplayer 音画同步播放

add_executable(player
#        src/video_play.cpp
#        src/audio_play.cpp
        src/avplayer.cpp
#        src/avsync/main.cpp
#        src/avsync/player.cpp
#        src/avsync/demux.cpp
#        src/avsync/video.cpp
#        src/avsync/audio.cpp
#        src/avsync/packet.cpp
#        src/avsync/frame.cpp
#        src/player.cpp
        )

target_include_directories(${PROJECT_NAME}
        PRIVATE
        ${PROJECT_SOURCE_DIR}/include
        ${AVCODEC_INCLUDE_DIR}
        ${AVFORMAT_INCLUDE_DIR}
        ${AVUTIL_INCLUDE_DIR}
        ${AVDEVICE_INCLUDE_DIR}
        ${AVFILTER_INCLUDE_DIR}
        ${POSTPROC_INCLUDE_DIR}
        ${SWRESAMPLE_INCLUDE_DIR}
        ${SWSCALE_INCLUDE_DIR}
        ${SDL_INCLUDE_DIR}
        )

target_link_libraries(${PROJECT_NAME}
        PRIVATE
        ${AVCODEC_LIBRARY}
        ${AVFORMAT_LIBRARY}
        ${AVUTIL_LIBRARY}
        ${AVDEVICE_LIBRARY}
        ${AVFILTER_LIBRARY}
        ${POSTPROC_LIBRARY}
        ${SWRESAMPLE_LIBRARY}
        ${SWSCALE_LIBRARY}
        ${SDL_LIBRARY}

        )
