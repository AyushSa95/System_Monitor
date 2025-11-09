cmake_minimum_required(VERSION 3.10)
project(SystemMonitor)

# Use modern C++
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Include headers
include_directories(include)

# Source files (as in your src directory)
set(SOURCES
    src/main.cpp
    src/cpu_monitor.cpp
    src/memory_monitor.cpp
    src/disk_monitor.cpp
    src/network_monitor.cpp
    src/utils.cpp
)

# Header files (as in your include directory)
set(HEADERS
    include/cpu_monitor.h
    include/memory_monitor.h
    include/disk_monitor.h
    include/network_monitor.h
    include/utils.h
)

# Create the executable
add_executable(SystemMonitor ${SOURCES} ${HEADERS})

# Link PDH library (for Windows performance counters)
if(WIN32)
    target_link_libraries(SystemMonitor pdh)
endif()
