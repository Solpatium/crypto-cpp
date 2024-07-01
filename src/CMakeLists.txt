set(need_boost FALSE)

if(CMAKE_CXX_COMPILER_ID STREQUAL "MSVC")
    set(need_boost TRUE)
endif()

if(${need_boost})
    add_subdirectory(third_party/boost)
endif()

add_subdirectory(starkware)