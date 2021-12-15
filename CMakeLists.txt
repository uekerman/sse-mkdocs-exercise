cmake_minimum_required(VERSION "3.12")

project("documentationexample" VERSION 0.1.0)

find_package(Boost
  1.65.1
  REQUIRED
  filesystem
  )

find_package(yaml-cpp
  0.6.0
  REQUIRED
  )

add_library(documentationexamplelib src/filesystem/filesystem.cpp src/flatset/flatset.cpp src/yamlParser/yamlParser.cpp)

set_target_properties(documentationexamplelib
  PROPERTIES
    PUBLIC_HEADER src/filesystem/filesystem.hpp
    PUBLIC_HEADER src/flatset/flatset.hpp
    PUBLIC_HEADER src/yamlParser/yamlParser.hpp
  )

include_directories(${YAML_CPP_INCLUDE_DIR})

add_executable(documentationexample src/main.cpp)
target_link_libraries(documentationexample documentationexamplelib)
target_link_libraries(documentationexamplelib Boost::filesystem yaml-cpp)

target_include_directories(documentationexamplelib
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/documentationexamplelib
    PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/documentationexamplelib>
        $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}/documentationexamplelib>
  )

# Create install targets
include(GNUInstallDirs)
install(TARGETS documentationexample documentationexamplelib
  LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
  ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
  RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
  PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/documentationexample
  INCLUDES DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/documentationexample
  )
