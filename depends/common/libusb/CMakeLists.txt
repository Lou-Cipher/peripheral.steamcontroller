cmake_minimum_required(VERSION 3.1)
project(libusb)

include(ExternalProject)

ExternalProject_Add(
    libusb
    SOURCE_DIR          ${CMAKE_SOURCE_DIR}
    CONFIGURE_COMMAND   <SOURCE_DIR>/autogen.sh
                            --prefix=${OUTPUT_DIR}
                            --enable-static
                            --disable-shared
                            --disable-examples-build
                            --disable-tests-build
    INSTALL_COMMAND     ""
    BUILD_IN_SOURCE     1
)

install(CODE "execute_process(COMMAND make install WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})")
