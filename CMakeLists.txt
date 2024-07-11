cmake_minimum_required ( VERSION 3.8 )

project ( RTWeekend LANGUAGES CXX )

set ( CMAKE_CXX_STANDARD 11 )
set ( CMAKE_CXX_STANDARD_REQUIRED ON )
set ( CMAKE_CXX_EXTENSIONS OFF )

set ( CMAKE_EXPORT_COMPILE_COMMANDS ON )

set ( SOURCE_ONE_WEEKEND
    src/main.cpp 
)

include_directories(src)

message ( STATUS "Compiler ID: " ${CMAKE_CXX_COMPILER_ID})
message ( STATUS "Release flags: " ${CMAKE_CXX_FLAGS_RELEASE})
message ( STATUS "Debug flags: " ${CMAKE_CXX_FLAGS_DEBUG})

if (CMAKE_CXX_COMPILER_ID MATCHES "Clang")
    add_compile_options(-Wnon-virtual-dtor) # Class has virtual functions, but its destructor is not virtual
    add_compile_options(-Wreorder) # Data member will be initialized after [other] data member
    add_compile_options(-Wsometimes-uninitialized) # Variable improperly initialized
    add_compile_options(-Wunused-variable) # Variable is defined but unused
endif()

add_executable(inOneWeekend ${SOURCE_ONE_WEEKEND})
