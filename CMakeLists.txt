cmake_minimum_required(VERSION 3.17)
project(chat_app)

set(SOURCES 
    ${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp
)


add_executable(chat_app ${SOURCES})

target_include_directories( chat_app PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} )

target_compile_options( chat_app PRIVATE 
    $<$<CONFIG:Debug>:
        -fsanitize=address,leak
    >
)

target_link_options( chat_app PRIVATE 
    $<$<CONFIG:Debug>:
        -fsanitize=address,leak
    >
)

target_compile_features(chat_app
    PRIVATE
        cxx_std_20
)

