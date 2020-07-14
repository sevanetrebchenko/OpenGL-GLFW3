cmake_minimum_required(VERSION 3.16)
project(OpenGL_GLFW3)

set(CMAKE_CXX_STANDARD 14)
set (SOURCE_FILES main.cpp)
add_executable(${PROJECT_NAME} ${SOURCE_FILES})

# Add glad to project.
add_subdirectory(glad)
target_include_directories(glad PRIVATE glad/include)
target_link_libraries(${PROJECT_NAME} "glad" "${CMAKE_DL_LIBS}")

# Add GLFW3 to project.
add_subdirectory(glfw-3.3.2)
# Disable building GLFW3 tests, examples and documentation
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
# Link library into executable.
target_link_libraries(${PROJECT_NAME} glfw)
