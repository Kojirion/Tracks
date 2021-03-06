project(Tracks)
cmake_minimum_required(VERSION 2.8)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -std=c++14")

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake")

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-unused-local-typedefs") #suppress warning in Aurora in Thor

find_package(SFML 2 REQUIRED graphics window system)
find_package(Thor 2 REQUIRED)
find_package(SFGUI REQUIRED)

include_directories(${SFML_INCLUDE_DIR} ${THOR_INCLUDE_DIR} ${SFGUI_INCLUDE_DIR})

set(HDRS
    Application.hpp
    Point.hpp
    Tracks.hpp
    TrackChunk.hpp
    FrameCounter.hpp
    Wagon.hpp
    Window.hpp
    Score.hpp
)

set(SRCS
    Application.cpp
    main.cpp
    Tracks.cpp
    TrackChunk.cpp
    FrameCounter.cpp
    Wagon.cpp
    Score.cpp
)

add_executable(${PROJECT_NAME} ${HDRS} ${SRCS})

target_link_libraries(${PROJECT_NAME} ${SFML_LIBRARIES} ${THOR_LIBRARY} ${SFGUI_LIBRARY})

install(TARGETS ${PROJECT_NAME} DESTINATION ${CMAKE_INSTALL_PREFIX})
FILE(GLOB images "*.png")
install(FILES ${images} DESTINATION ${CMAKE_INSTALL_PREFIX})
install(FILES KBZipaDeeDooDah.ttf DESTINATION ${CMAKE_INSTALL_PREFIX})
