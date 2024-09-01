cmake_minimum_required(VERSION 3.27)
project(TeaEngine)

set(CMAKE_CXX_STANDARD 17)


include_directories(${CMAKE_SOURCE_DIR}/Dependencies/include)

set(SOURCES
        library.cpp
        Dependencies/include/ImGui/imgui_impl_opengl3.cpp
        Dependencies/include/ImGui/imgui_impl_win32.cpp
        Dependencies/include/glad/glad.c
)

set(HEADERS
        Dependencies/include/ImGui/imconfig.h
        Dependencies/include/ImGui/imgui.h
        Dependencies/include/ImGui/imgui_impl_opengl3.h
        Dependencies/include/ImGui/imgui_impl_opengl3_loader.h
        Dependencies/include/ImGui/imgui_impl_win32.h
        Dependencies/include/ImGui/imgui_internal.h
        Dependencies/include/ImGui/imgui_stdlib.h
        Dependencies/include/ImGui/imstb_rectpack.h
        Dependencies/include/ImGui/imstb_textedit.h
        Dependencies/include/ImGui/imstb_truetype.h
)

add_library(TeaEngine STATIC ${SOURCES})
set(LIBRARY_DIR ${CMAKE_SOURCE_DIR}/Dependencies/lib)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /MD")

target_link_libraries(TeaEngine PRIVATE
        opengl32
        ${LIBRARY_DIR}/imgui.lib
        ${LIBRARY_DIR}/glfw3.lib
        ${LIBRARY_DIR}/glfw3_mt.lib
        ${LIBRARY_DIR}/glfw3dll.lib
)


link_directories(${LIBRARY_DIR})

target_include_directories(TeaEngine PRIVATE
        ${CMAKE_SOURCE_DIR}/Dependencies/include
)
