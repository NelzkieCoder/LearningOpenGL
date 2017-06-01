cmake_minimum_required(VERSION 3.7)
project(GLFW_OpenGL)

set(CMAKE_CXX_STANDARD 11)

#set(SOURCE_FILES main.cpp Shader.cpp Headers/Shader.h Headers/stb_image.h Headers/filesystem.h Headers/root_directory.h stb_image.cpp)


# for exercises to run
set(SOURCE_FILES "Chapter1/3.1 Textures/Exercises/3.2_Textures.cpp" Headers/Shader.h  stb_image.cpp)


# for main files
#set(SOURCE_FILES "Chapter1/3.1 Textures/3.2_Textures.cpp" Headers/Shader.h  stb_image.cpp)


add_executable(GLFW_OpenGL ${SOURCE_FILES})



add_subdirectory(${CMAKE_SOURCE_DIR}/glfw-3.2.1/)

MESSAGE(${CMAKE_SOURCE_DIR})



set(SOIL_LIBRARY ${CMAKE_SOURCE_DIR}/Libraries/SOIL/lib/libSOIL.a)
set(GLAD_LIB ${CMAKE_SOURCE_DIR}/Libraries/GLAD/libglad.a)

include_directories(${CMAKE_SOURCE_DIR}/Headers/)
include_directories(${CMAKE_SOURCE_DIR}/includes/glfw-3.2.1/include/)
include_directories(${CMAKE_SOURCE_DIR}/includes/GLM/include/)
include_directories(${CMAKE_SOURCE_DIR}/includes/SOIL/include/)
include_directories(${CMAKE_SOURCE_DIR}/includes/GLAD/include/)




target_link_libraries(GLFW_OpenGL ${GLAD_LIB})
target_link_libraries(GLFW_OpenGL glfw ${OPENGL_glu_LIBRARY} ${GLFW_LIBRARIES} ${SOIL_LIBRARY})


#find_package(GLEW REQUIRED)
find_package(OpenGL REQUIRED)

#link_libraries(${GLEW_LIBRARIES})
#if (APPLE)
#    target_link_libraries(GLFW_OpenGL "-framework OpenGL")
#    target_link_libraries(GLFW_OpenGL  -lGLEW )
#    target_link_libraries(GLFW_OpenGL  -lGLEW )
#endif()
