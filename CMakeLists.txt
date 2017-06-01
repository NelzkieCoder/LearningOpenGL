cmake_minimum_required(VERSION 3.7)
project(GLFW_OpenGL)

set(CMAKE_CXX_STANDARD 11)

#set(SOURCE_FILES main.cpp Shader.cpp Headers/Shader.h Headers/stb_image.h Headers/filesystem.h Headers/root_directory.h stb_image.cpp)

set(SOURCE_FILES "Chapter1/1.2 Triangle_Indices/1.2_Triangle_Indices.cpp"  stb_image.cpp)


add_executable(GLFW_OpenGL ${SOURCE_FILES})



add_subdirectory(${CMAKE_SOURCE_DIR}/glfw-3.2.1/)
#add_subdirectory(/Users/skadush/Documents/GLFW_OpenGL/SOIL_Master/)
MESSAGE(${CMAKE_SOURCE_DIR})


set(SOIL_ROOT_DIR ${CMAKE_SOURCE_DIR}/SOIL_Builds/ )
set(SOIL_LIBRARY ${CMAKE_SOURCE_DIR}/Libraries/SOIL/lib/libSOIL.a)
set(GLAD_LIB ${CMAKE_SOURCE_DIR}/Libraries/GLAD/libglad.a)


include_directories(${CMAKE_SOURCE_DIR}/includes/glfw-3.2.1/include/)
include_directories(${CMAKE_SOURCE_DIR}/includes/GLM/include/)
include_directories(${CMAKE_SOURCE_DIR}/includes/SOIL/include/)
include_directories(${CMAKE_SOURCE_DIR}/includes/GLAD/include/)



target_link_libraries(GLFW_OpenGL ${SOIL_LIBRARY})
target_link_libraries(GLFW_OpenGL ${GLAD_LIB})
target_link_libraries(GLFW_OpenGL glfw ${OPENGL_glu_LIBRARY} ${GLFW_LIBRARIES} ${SOIL_LIBRARY})


find_package(GLEW REQUIRED)
find_package(OpenGL REQUIRED)

link_libraries(${GLEW_LIBRARIES})
if (APPLE)
    target_link_libraries(GLFW_OpenGL "-framework OpenGL")
    target_link_libraries(GLFW_OpenGL  -lGLEW )
    target_link_libraries(GLFW_OpenGL  -lGLEW )
endif()
