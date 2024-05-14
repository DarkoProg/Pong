cmake_minimum_required(VERSION 3.29)

#set project name
project(Pong VERSION 0.1)


add_executable(${PROJECT_NAME} Libraries/main.cpp)

#compile setup
target_compile_features(Pong
    PRIVATE
    cxx_std_17
    )

#add for release
#target_compile_options(Pong PRIVATE -O2)

target_link_libraries(Pong
    PRIVATE
    glfw vulkan dl pthread X11 Xxf86vm Xrandr Xi
    )

add_custom_target(run
    COMMAND Pong
    DEPENDS Pong
    WORKING_DIRECTORY ${CMAKE_PROJECT_DIR}
    )

file(MAKE_DIRECTORY build/Shaders)
