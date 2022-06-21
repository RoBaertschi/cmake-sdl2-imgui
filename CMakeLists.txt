cmake_minimum_required(VERSION 3.0.0)
project(sdl2-imgui VERSION 0.1.0)
set(EXPORT_COMPILE_COMMANDS 1)

include(CTest)
enable_testing()

set(SDL2PP_WITH_IMAGE ON) # if you need SDL_image support
set(SDL2PP_WITH_MIXER ON) # if you need SDL_mixer support
set(SDL2PP_WITH_TTF ON) # if you need SDL_ttf support
add_subdirectory(extlib/libSDL2pp)
include_directories(extlib/imgui)

if(NOT WIN32)
    find_package(OpenGL REQUIRED)
endif()

add_executable(sdl2-imgui main.cpp)
target_link_libraries(sdl2-imgui SDL2pp::SDL2pp)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
