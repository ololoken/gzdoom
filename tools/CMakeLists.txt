cmake_minimum_required( VERSION 3.16 )

function(make_release_only)
    if(CMAKE_CONFIGURATION_TYPES)
        set(ConfigTypes ${CMAKE_CONFIGURATION_TYPES})
        list(REMOVE_ITEM ConfigTypes "Release")
    else()
        set(ConfigTypes "Debug;MinSizeRel;RelWithDebInfo")
    endif()

    foreach(Config IN LISTS ConfigTypes)
        string(TOUPPER "${Config}" ConfigUpper)
        set("CMAKE_C_FLAGS_${ConfigUpper}" "${CMAKE_C_FLAGS_RELEASE}" PARENT_SCOPE)
    endforeach()
endfunction()

add_subdirectory( re2c )
add_subdirectory( lemon )
add_subdirectory( zipdir )

set( CROSS_EXPORTS ${CROSS_EXPORTS} PARENT_SCOPE )
