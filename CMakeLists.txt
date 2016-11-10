cmake_minimum_required(VERSION 2.6)
project(astar)

# Add all files in src to be builded
file(GLOB astar_SRC
    "*.h"
    "*.cpp"
)

# Add list of files to executable
add_executable(astar ${astar_SRC})

# set path to our custom CMAKE scripts
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${PROJECT_SOURCE_DIR}/CMake/Modules")

find_package(SDL2 REQUIRED)
find_package(SDL2_image REQUIRED)
find_package(SDL2_ttf REQUIRED)
find_package(SDL2_gfx REQUIRED)

include_directories(
    ${SDL2_IMAGE_INCLUDE_DIR}
    ${SDL2_INCLUDE_DIR}
    ${SDL2_TTF_INCLUDE_DIR}
    ${SDL2_GFX_INCLUDE_DIR}
)

target_link_libraries(astar ${SDL2_LIBRARY})
target_link_libraries(astar ${SDL2_IMAGE_LIBRARIES})
target_link_libraries(astar ${SDL2_TTF_LIBRARIES})
target_link_libraries(astar ${SDL2_GFX_LIBRARIES})

# Set flags for cmake about c++ version and debug/release warnings
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -Wall")
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -Wall")

install(TARGETS astar RUNTIME DESTINATION bin)
