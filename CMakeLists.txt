cmake_minimum_required(VERSION 3.10)

project(SPHProject VERSION 1.0)

# Specify the C compiler
set(CMAKE_C_COMPILER mpicc)


# Enable C11 standard
set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED True)

# Set the CMake flags (equivalent to CFLAGS)
set(CMAKE_C_FLAGS "-DGLFW -g -O0 -pg -I/usr/local/include -I/usr/include/libdrm -fcommon -Wimplicit-function-declaration")
# Set the CMake flags (equivalent to CFLAGS)
#set(CMAKE_C_FLAGS_DEBUG "-g -O0 -ffast-math -pg -I/usr/local/include -I/usr/include/libdrm -fcommon")
#set(CMAKE_C_FLAGS_RELEASE "-O3 -ffast-math -I/usr/local/include -I/usr/include/libdrm -fcommon")


# Include directories
include_directories(/usr/include/freetype2)

# Source files
set(SOURCE_FILES
        src/ogl_utils.c
        src/dividers_gl.c
        src/liquid_gl.c
        src/exit_menu_gl.c
        src/image_gl.c
        src/cursor_gl.c
        src/rectangle_gl.c
        src/lodepng.c
        src/background_gl.c
        src/font_gl.c
        src/glfw_utils.c
        src/particles_gl.c
        src/mover_gl.c
        src/controls.c
        src/renderer.c
        src/geometry.c
        src/hash.c
        src/communication.c
        src/fluid.c
)

# Output directory
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# Add the executable
add_executable(sph.out ${SOURCE_FILES})

# Link libraries
target_link_libraries(sph.out glfw GL GLU X11 GLEW Xxf86vm Xrandr Xi freetype m)

## Custom target for cleaning
#add_custom_target(clean
#        COMMAND ${CMAKE_COMMAND} -E remove -f sph.out
#        COMMAND ${CMAKE_COMMAND} -E remove_directory ${CMAKE_BINARY_DIR}/bin
#)

