cmake_minimum_required(VERSION 3.30)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

project(MYSPECIALLIB VERSION 1.0)

add_library(myspeciallib src/mylibgreet.cpp)
set_target_properties(myspeciallib PROPERTIES PUBLIC_HEADER src/mylibgreet.h)

include(GNUInstallDirs)
install(TARGETS myspeciallib
    EXPORT myspeciallibtargets
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    FILE_SET HEADERS DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
    )

install(EXPORT myspeciallibtargets
    FILE myspeciallib-config.cmake
    NAMESPACE myspeciallib::
    DESTINATION share/
)
