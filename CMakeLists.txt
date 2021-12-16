cmake_minimum_required(VERSION 3.5)
project(cool_data_structures)

set(CMAKE_CXX_STANDARD 17)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

add_subdirectory(abseil-cpp)

include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/e2239ee6043f73722e7aa812a459f54a28552929.zip
)
FetchContent_MakeAvailable(googletest)
enable_testing()

include(GoogleTest)

add_library(unrolled_linked_list "")
set_target_properties(unrolled_linked_list PROPERTIES LINKER_LANGUAGE CXX)
target_compile_options(unrolled_linked_list PRIVATE -fsanitize=address,undefined)
target_link_libraries(unrolled_linked_list PRIVATE -fsanitize=address,undefined)
target_compile_options(unrolled_linked_list PRIVATE -fno-omit-frame-pointer)
target_link_libraries(unrolled_linked_list PRIVATE -fno-omit-frame-pointer)
target_compile_options(unrolled_linked_list PRIVATE -g)
target_link_libraries(unrolled_linked_list PRIVATE -g)

add_executable(unrolled_linked_list_test "")
target_link_libraries(
  unrolled_linked_list_test
  PRIVATE
  unrolled_linked_list
  gtest_main
)
gtest_discover_tests(unrolled_linked_list_test)

add_subdirectory(unrolled_linked_list)