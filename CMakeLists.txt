CMAKE_MINIMUM_REQUIRED(VERSION 3.0)
PROJECT(bemenu C)
SET(BEMENU_NAME "bemenu")
SET(BEMENU_DESCRIPTION "Dynamic menu library and client program inspired by dmenu")
SET(BEMENU_VERSION "0.3.0")
SET(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/CMake)

OPTION(BEMENU_CURSES_RENDERER "Build curses backend" ON)
OPTION(BEMENU_X11_RENDERER "Build X11 backend" ON)
OPTION(BEMENU_WAYLAND_RENDERER "Build wayland renderer" OFF)

INCLUDE(CTest)
INCLUDE(GetGitRevisionDescription)
get_git_head_revision(GIT_REFSPEC GIT_SHA1)

# C99 and _GNU_SOURCE for secure_getenv
ADD_DEFINITIONS(-std=c99 -D_GNU_SOURCE)

# Compile library
ADD_SUBDIRECTORY(lib)

# Compile client
ADD_SUBDIRECTORY(client)

# Compile tests
ADD_SUBDIRECTORY(test)

# Generate documentation (make doxygen)
ADD_SUBDIRECTORY(doxygen)
ADD_SUBDIRECTORY(man)

# vim: set ts=8 sw=4 tw=0
