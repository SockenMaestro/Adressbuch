cmake_minimum_required(VERSION 3.16)

project(Adressbuch LANGUAGES C)

# C Standard setzen
set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS OFF)

# Alle Quell- und Headerdateien angeben
set(SOURCES
  src/main.c
  
  
)

# Executable definieren
add_executable(${PROJECT_NAME} ${SOURCES})

# Include-Verzeichnis hinzufügen, damit Header gefunden werden
target_include_directories(${PROJECT_NAME}
  PRIVATE ${CMAKE_SOURCE_DIR}/inc
)

# Einfache Warnungen einschalten
if (CMAKE_C_COMPILER_ID MATCHES "Clang|GNU")
  target_compile_options(${PROJECT_NAME} PRIVATE -Wall -Wextra -Wpedantic)
elseif (MSVC)
  target_compile_options(${PROJECT_NAME} PRIVATE /W4)
endif()