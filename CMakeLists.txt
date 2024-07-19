set(TARGET_NAME neural_network_models)

install(DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/neural_network_models/
    DESTINATION bin/plugins/resources/neural_network_models
    FILES_MATCHING PATTERN "*"
)
