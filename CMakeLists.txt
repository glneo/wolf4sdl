cmake_minimum_required(VERSION 2.6)
project(Wolf4SDL)

set(WOLF4SDL_SOURCES
	src/fmopl.cpp
	src/id_ca.cpp
	src/id_in.cpp
	src/id_pm.cpp
	src/id_sd.cpp
	src/id_us_1.cpp
	src/id_vh.cpp
	src/id_vl.cpp
	src/signon.cpp
	src/wl_act1.cpp
	src/wl_act2.cpp
	src/wl_agent.cpp
	src/wl_atmos.cpp
	src/wl_cloudsky.cpp
	src/wl_debug.cpp
	src/wl_dir3dspr.cpp
	src/wl_draw.cpp
	src/wl_floorceiling.cpp
	src/wl_game.cpp
	src/wl_inter.cpp
	src/wl_main.cpp
	src/wl_menu.cpp
	src/wl_parallax.cpp
	src/wl_play.cpp
	src/wl_shade.cpp
	src/wl_state.cpp
	src/wl_text.cpp
)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake")

add_executable(wolf4sdl ${WOLF4SDL_SOURCES} ${WOLF4SDL_HEADERS})

find_package(SDL REQUIRED)
target_include_directories(wolf4sdl PUBLIC ${SDL_INCLUDE_DIR})
target_link_libraries(wolf4sdl m ${SDL_LIBRARY})

find_package(SDL_mixer REQUIRED)
target_include_directories(wolf4sdl PUBLIC ${SDL_MIXER_INCLUDE_DIRS})
target_link_libraries(wolf4sdl ${SDL_MIXER_LIBRARIES})

target_compile_options(wolf4sdl PRIVATE -g;-ffast-math;-Wall)
install(TARGETS wolf4sdl RUNTIME DESTINATION bin)
