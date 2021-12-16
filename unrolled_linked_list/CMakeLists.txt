target_sources(unrolled_linked_list
    PRIVATE 
    ${CMAKE_CURRENT_LIST_DIR}/unrolled_linked_list.hpp
)

target_sources(unrolled_linked_list_test
    PRIVATE 
    ${CMAKE_CURRENT_LIST_DIR}/unrolled_linked_list_test.cpp
)

target_include_directories(unrolled_linked_list PRIVATE ${CMAKE_CURRENT_LIST_DIR})
target_include_directories(unrolled_linked_list_test PRIVATE ${CMAKE_CURRENT_LIST_DIR})