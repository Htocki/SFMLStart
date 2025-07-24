cmake_minimum_required(VERSION 4.0.3)

project("application"
  LANGUAGES CXX
  VERSION 1.0
)

if (CMAKE_COMPILER_IS_GNUCXX)
  add_definitions (-Wall -pedantic)
endif ()

if (CMAKE_PROJECT_NAME STREQUAL PROJECT_NAME)
  include (CTest)
endif ()

enable_testing()

include(FetchContent)

FetchContent_Declare(
  sfml
  GIT_REPOSITORY https://github.com/SFML/SFML.git
  GIT_TAG        3.0.1
)
FetchContent_MakeAvailable(sfml)

FetchContent_Declare(
  googletest
  GIT_REPOSITORY https://github.com/google/googletest
  GIT_TAG        v1.17.0
)
FetchContent_MakeAvailable(googletest)

add_executable(executable Main.cpp)

target_link_libraries(executable
  PRIVATE
    SFML::Graphics
    SFML::Audio
    SFML::Network
)
