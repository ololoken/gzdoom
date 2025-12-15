cmake_minimum_required( VERSION 3.16 )

if (NOT CMAKE_SYSTEM MATCHES "Emscripten")

add_subdirectory( libraries/bzip2 )
set( BZIP2_INCLUDE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/libraries/bzip2" )
set( BZIP2_LIBRARIES bz2 )
set( BZIP2_LIBRARY bz2 )

add_subdirectory( libraries/miniz )

set( LZMA_INCLUDE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/libraries/lzma/C" )

add_subdirectory( libraries/lzma )

else ()
	add_executable( zipdir zzipdir.c)
endif ()
if( NOT CMAKE_CROSSCOMPILING )
	include_directories( SYSTEM "${BZIP2_INCLUDE_DIR}" "${LZMA_INCLUDE_DIR}" )
	add_executable( zipdir
		zipdir.c )
	target_link_libraries( zipdir miniz ${BZIP2_LIBRARIES} lzma )
	set( CROSS_EXPORTS ${CROSS_EXPORTS} zipdir PARENT_SCOPE )
endif()
