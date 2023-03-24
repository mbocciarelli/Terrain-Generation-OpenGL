cmake_minimum_required(VERSION 3.24)
set(CMAKE_TOOLCHAIN_FILE ${CMAKE_SOURCE_DIR}/vcpkg/scripts/buildsystems/vcpkg.cmake)

project(messing-with-OpenGL)

set(CMAKE_CXX_STANDARD 20)

find_package(glfw3 3.3 REQUIRED)
find_package(OpenGL REQUIRED)
find_package(GLEW REQUIRED)
find_package(glm REQUIRED)
find_package(unofficial-noise REQUIRED)

configure_file(res/grass.png ${CMAKE_CURRENT_BINARY_DIR}/Debug/res/grass.png COPYONLY)
configure_file(res/heightmap.bmp ${CMAKE_CURRENT_BINARY_DIR}/Debug/res/heightmap.bmp COPYONLY)
configure_file(res/mountains.jpg ${CMAKE_CURRENT_BINARY_DIR}/Debug/res/mountains.jpg COPYONLY)

configure_file(src/shaders/terrain.frag ${CMAKE_CURRENT_BINARY_DIR}/Debug/src/shaders/terrain.frag COPYONLY)
configure_file(src/shaders/terrain.vert ${CMAKE_CURRENT_BINARY_DIR}/Debug/src/shaders/terrain.vert COPYONLY)

add_executable(messing-with-OpenGL src/main.cpp src/framework/texture.cpp src/utils/imageloader.cpp src/utils/noiseutils.cpp src/utils/stb_image.cpp)

target_link_libraries(messing-with-OpenGL PRIVATE glfw)
target_link_libraries(messing-with-OpenGL PRIVATE OpenGL::GL)
target_link_libraries(messing-with-OpenGL PRIVATE GLEW::GLEW)
target_link_libraries(messing-with-OpenGL PRIVATE glm::glm)
target_link_libraries(messing-with-OpenGL PRIVATE unofficial::noise::noise)

