########## LFAST Mount Driver ##############
# do the replacement in the config.h and LFAST_Mount.xml
# do the replacement in the config.h
configure_file(
    ${CMAKE_CURRENT_SOURCE_DIR}/config.h.cmake
    ${CMAKE_CURRENT_BINARY_DIR}/config.h
)

# do the replacement in the driver's xml file
configure_file(
    ${CMAKE_CURRENT_SOURCE_DIR}/Tempest_Weather.xml.cmake
    ${CMAKE_CURRENT_BINARY_DIR}/Tempest_Weather.xml
)

# set our include directories to look for header files
include_directories( ${CMAKE_BINARY_DIR})
include_directories( ${CMAKE_CURRENT_BINARY_DIR})
include_directories( ${CMAKE_CURRENT_SOURCE_DIR})

# tell cmake to build our executable
add_executable(
    Tempest_Weather
    Tempest_Weather.cpp
)

# and link it to these libraries
target_link_libraries(
    Tempest_Weather
    ${INDI_LIBRARIES}
    ${NOVA_LIBRARIES}
    ${GSL_LIBRARIES}
)

# tell cmake where to install our executable
install(TARGETS Tempest_Weather RUNTIME DESTINATION bin)

# and where to put the driver's xml file.
install(
    FILES
    ${CMAKE_CURRENT_BINARY_DIR}/Tempest_Weather.xml
    DESTINATION ${INDI_DATA_DIR}
)
