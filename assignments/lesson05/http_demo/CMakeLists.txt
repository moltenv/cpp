cmake_minimum_required(VERSION 3.20...3.24)
project(lesson05_http_demo LANGUAGES CXX)

find_package(CURL REQUIRED)

# FetchContent и версия из lesson04; компактный архив вместо Git-истории.
include(FetchContent)
FetchContent_Declare(nlohmann_json
    URL https://github.com/nlohmann/json/releases/download/v3.11.3/json.tar.xz
)
FetchContent_MakeAvailable(nlohmann_json)

add_executable(local_chat main.cpp)
target_compile_features(local_chat PRIVATE cxx_std_17)
set_target_properties(local_chat PROPERTIES CXX_EXTENSIONS OFF)
target_link_libraries(local_chat PRIVATE CURL::libcurl nlohmann_json::nlohmann_json)
