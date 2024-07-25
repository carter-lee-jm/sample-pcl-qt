cmake_minimum_required(VERSION 3.5)

project(pcl_colorize_cloud)

# init_qt: Let's do the CMake job for us
set(CMAKE_AUTOMOC ON) # For meta object compiler
set(CMAKE_AUTORCC ON) # Resource files
set(CMAKE_AUTOUIC ON) # UI files

# Find includes in corresponding build directories
set(CMAKE_INCLUDE_CURRENT_DIR ON)

# Find the QtWidgets library
find_package(Qt6 QUIET COMPONENTS Widgets Core openglwidgets)
qt_standard_project_setup()
set(QTX Qt6)



find_package(VTK REQUIRED)
find_package(PCL CONFIG REQUIRED)

include_directories(${PCL_INCLUDE_DIRS})
add_definitions(${PCL_DEFINITIONS})
find_package(Boost REQUIRED COMPONENTS thread system)

set(project_SOURCES main.cpp pclviewer.cpp)

add_executable(${PROJECT_NAME} ${project_SOURCES})

target_link_libraries(${PROJECT_NAME} ${PCL_LIBRARIES} ${QTX}::Widgets Boost::thread Boost::system)