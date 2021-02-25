cmake_minimum_required(VERSION 3.1)
project(graphcpp VERSION 1.0.0)


if (NOT CMAKE_CXX_STANDARD)
    set(CMAKE_CXX_STANDARD 14)
elseif (CMAKE_CXX_STANDARD LESS 11)
    message(WARNING "CMAKE_CXX_STANDARD has been set to '${CMAKE_CXX_STANDARD}' which is lower than the minimum required standard (c++14).")
endif ()
message(STATUS "Using c++ standard c++${CMAKE_CXX_STANDARD}")
set(CMAKE_CXX_STANDARD_REQUIRED ON)

message (STATUS "CMake version: ${CMAKE_VERSION}")
message (STATUS "Project version: ${PROJECT_VERSION}")

set(GRAPHCPP_SRC ${PROJECT_SOURCE_DIR}/src/graph.cpp)
source_group(src FILES ${GRAPHCPP_SRC})

set(GRAPHCPP_INC ${PROJECT_SOURCE_DIR}/include/graph/graph.hpp)
source_group(include FILES ${GRAPHCPP_INC})

set(GRAPHCPP_DOC 
    README.md
)
source_group(doc FILES ${GRAPHCPP_DOC})

set(GRAPHCPP_SCRIPTS
    .gitignore
    build.sh
)
source_group(scripts FILES ${GRAPHCPP_SCRIPTS})

add_library(graphcpp ${GRAPHCPP_SRC} ${GRAPHCPP_INC} ${GRAPHCPP_SCRIPTS} ${GRAPHCPP_DOC})

target_include_directories(graphcpp PUBLIC ${PROJECT_SOURCE_DIR}/include)
