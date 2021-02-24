cmake_minimum_required (VERSION 3.18)

project ("project-name")

set(CXX_STANDARD 17) # Supported values are 98, 11, 14, 17, 20, 23

set(CMAKE_EXE_LINKER_FLAGS "/NODEFAULTLIB:MSVCRT")

add_definitions(-D_CRT_SECURE_NO_WARNINGS)

include_directories(Resources/Libraries/<a-lib-name>/include
                    Resources/Libraries/<b-lib-name>/include)

link_directories(Resources/Libraries/<a-lib-name>/lib/x64 
                 Resources/Libraries/<b-lib-name>/lib/x64)

link_libraries(<a-lib-name>.lib 
               <b-lib-name>.lib)

file(GLOB SOURCE_FILES *.c)

foreach(SOURCE_PATH ${SOURCE_FILES})

    get_filename_component(EXECUTABLE_NAME ${SOURCE_PATH} NAME_WE)

    add_executable(${EXECUTABLE_NAME} ${SOURCE_PATH})

    add_custom_command(TARGET ${EXECUTABLE_NAME} POST_BUILD
                       COMMAND ${CMAKE_COMMAND} -E copy_if_different "${CMAKE_SOURCE_DIR}/Resources/Libraries/<a-lib-name>/bin/x64/<a-lib-name>.dll" 
                                                                     "${CMAKE_BINARY_DIR}/<a-lib-name>.dll")

endforeach(SOURCE_PATH ${SOURCE_FILES})