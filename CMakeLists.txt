cmake_minimum_required(VERSION 3.13)
project(asciichess CXX)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)


# add_library(chessboard OBJECT chessboard.cpp chessboard.hpp)
# add_library(piece OBJECT piece.cpp piece.hpp)
# add_library(console_visitor OBJECT console_visitor.cpp console_visitor.hpp)

add_executable(${PROJECT_NAME}
    main.cpp
    chessboard.cpp
    piece.cpp
    console_visitor.cpp
    position.cpp
    game_rules.cpp

    chessboard.hpp
    piece.hpp
    settings.hpp
    console_visitor.hpp
    position.hpp
    game_rules.hpp
)
target_include_directories(${PROJECT_NAME}
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}
)
target_compile_features(${PROJECT_NAME}
    PUBLIC
        cxx_std_17
)
target_compile_options(${PROJECT_NAME}
    PRIVATE
        -Wall
        -Wextra
        -pedantic
        -Weffc++
        -Wshadow
        $<$<CXX_COMPILER_ID:GNU>:-Wmisleading-indentation>
        $<$<CONFIG:Debug>:-ggdb3>
)
target_compile_options(${PROJECT_NAME}
    PUBLIC
        -fuse-ld=gold
)
target_link_libraries(${PROJECT_NAME}
    PRIVATE
        -lstdc++fs
)