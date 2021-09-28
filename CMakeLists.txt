cmake_minimum_required(VERSION 3.17)
project(MyFBXStudy01)

set(CMAKE_CXX_STANDARD 20)

set(PROJECT_NAME MyFBXStudy01)

set(FBX_PLUGIN_PATH FBXPlugin)
set(IS_DEBUG ${CMAKE_BUILD_TYPE} STREQUAL Debug)
if (IS_DEBUG)
    set(LIBPATH ${FBX_PLUGIN_PATH}/lib/vs2019/x64/debug)
else (IS_DEBUG)
    set(LIBPATH ${FBX_PLUGIN_PATH}/lib/vs2019/x64/release)
endif (IS_DEBUG)

set(LIBS "libfbxsdk-md.lib;libxml2-md.lib;zlib-md.lib;")

include_directories(BEFORE "${FBX_PLUGIN_PATH}/include")
link_directories(${LIBPATH})

file(GLOB SRC_FILES "src/*.h" "src/*.cpp" "src/*.cxx")
add_executable(${PROJECT_NAME} ${SRC_FILES})

target_link_libraries(${PROJECT_NAME} "${LIBS}")
