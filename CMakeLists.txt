cmake_minimum_required(VERSION 3.5...3.25)
project(15Puzzle LANGUAGES CXX)

# 1. Настройка версии и метаданных для пакета
set(PACKAGE_VERSION "1.0.0")
set(CPACK_PACKAGE_NAME "15-puzzle")
set(CPACK_PACKAGE_VENDOR "Your Name")
set(CPACK_PACKAGE_DESCRIPTION "15-Puzzle Game using SFML")
set(CPACK_PACKAGE_CONTACT "your.email@example.com")

# 2. Подключение необходимых модулей
include(FetchContent)
include(CPack)

# 3. Настройка SFML
set(SFML_VERSION 2.6.1)

find_package(SFML ${SFML_VERSION} REQUIRED COMPONENTS graphics window system)

# 4. Копирование ресурсов с проверкой
if(EXISTS ${CMAKE_CURRENT_SOURCE_DIR}/images)
    file(COPY ${CMAKE_CURRENT_SOURCE_DIR}/images DESTINATION ${CMAKE_CURRENT_BINARY_DIR})
    message(STATUS "Ресурсы images скопированы")
else()
    message(WARNING "Папка images не найдена!")
endif()

# 5. Создание исполняемого файла
add_executable(15puzzle main.cpp)
target_compile_features(15puzzle PRIVATE cxx_std_17)
target_include_directories(15puzzle PRIVATE ${SFML_INCLUDE_DIR})

# 6. Линковка SFML
target_link_libraries(15puzzle PRIVATE sfml-graphics sfml-window sfml-system)

# 7. Установка в систему
install(TARGETS 15puzzle 
    RUNTIME DESTINATION bin
    BUNDLE DESTINATION bin
)

# 8. Установка ресурсов
if(EXISTS ${CMAKE_CURRENT_SOURCE_DIR}/images)
    install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/images
        DESTINATION share/${PROJECT_NAME}
    )
endif()

# 9. Дополнительные настройки для Windows
if(WIN32)
    # Копирование DLL
    add_custom_command(TARGET 15puzzle POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_if_different
        "$<TARGET_FILE:sfml-graphics>"
        "$<TARGET_FILE:sfml-window>"
        "$<TARGET_FILE:sfml-system>"
        "$<TARGET_FILE_DIR:15puzzle>"
        COMMENT "Копирование DLL SFML"
    )
    
    # Установка DLL при инсталляции
    install(FILES
        "$<TARGET_FILE:sfml-graphics>"
        "$<TARGET_FILE:sfml-window>"
        "$<TARGET_FILE:sfml-system>"
        DESTINATION bin
    )
endif()
