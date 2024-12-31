set(EXE_SOURCES
    "main.cc")
set(EXE_INCLUDES
    "./")


add_executable(${EXECUTABLE_NAME} ${EXE_SOURCES})

add_dependencies(${EXECUTABLE_NAME} SDL2)

find_package(SDL2 REQUIRED)

target_include_directories(${EXECUTABLE_NAME} PUBLIC
    ${EXE_INCLUDES})

target_include_directories(${EXECUTABLE_NAME} PUBLIC
    ${SDL2_INCLUDE_DIRS})

target_link_libraries(
    ${EXECUTABLE_NAME} ${SDL2_LIBRARIES})

#only with visual studio environment
set_target_properties(${EXECUTABLE_NAME} PROPERTIES
    VS_DEBUGGER_ENVIRONMENT "PATH=%PATH%;${SDL2_INSTALL_DIR}/bin"
)
# Assume SDL2_INSTALL_DIR contains the path to your SDL2 installation directory
# this only works if you actually build a releas version of sdl2
set(SDL2_DLL "${SDL2_INSTALL_DIR}/bin/sdl2.dll")

# the bat file of this
# set PATH=%PATH%;<path_to_your_sdl2_dll_folder>

add_custom_command(
    TARGET ${EXECUTABLE_NAME} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
    "${SDL2_DLL}"
    "$<TARGET_FILE_DIR:${EXECUTABLE_NAME}>"
)

if (ENABLE_WARNINGS)
    target_set_warnings(
        ${EXECUTABLE_NAME}
        ON
        OFF
    )
endif()
