cmake_minimum_required(VERSION 3.9)

project(cabman CXX)
# ReactOS cabinet manager

set(CMAKE_CXX_STANDARD 11)

find_package (ZLIB REQUIRED)

if(MINGW OR WIN32)
  set(CMAKE_CXX_FLAGS "${CMAKE_C_FLAGS} -mconsole -s")
endif(MINGW OR WIN32)

include_directories(${CMAKE_CURRENT_SOURCE_DIR})
#add_definitions(-DDBG)

list(APPEND SOURCE
    cabinet.cxx
    cabinet.h
    dfp.cxx
    dfp.h
    cabman.cxx
    cabman.h
    mszip.cxx
    mszip.h
    raw.cxx
    raw.h
    CCFDATAStorage.cxx
    CCFDATAStorage.h)

add_executable(${PROJECT_NAME} ${SOURCE})
target_link_libraries(${PROJECT_NAME} PRIVATE z)
install(TARGETS ${PROJECT_NAME} DESTINATION bin)

# add the uninstall support
configure_file(
	"${CMAKE_CURRENT_SOURCE_DIR}/cmake_uninstall.cmake.in"
	"${CMAKE_CURRENT_BINARY_DIR}/cmake_uninstall.cmake"
	@ONLY)
add_custom_target(uninstall
"${CMAKE_COMMAND}" -P "${CMAKE_CURRENT_BINARY_DIR}/cmake_uninstall.cmake")
