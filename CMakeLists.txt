cmake_minimum_required(VERSION 3.6)
project(discordpp)

set(CMAKE_CXX_STANDARD 11)

set(SOURCE_FILES discordpp/discordpp.hh src/discordpp.cc discordpp/bot.hh src/bot.cc)
add_library(${PROJECT_NAME} SHARED ${SOURCE_FILES})

add_subdirectory(lib/curlpp)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/lib/curlpp/include/)

target_include_directories (${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

find_package(Boost REQUIRED system)

INCLUDE_DIRECTORIES(${Boost_INCLUDE_DIRS})
TARGET_LINK_LIBRARIES(${PROJECT_NAME} ${Boost_LIBRARIES} curlpp curl pthread ssl crypto)
