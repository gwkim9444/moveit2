set(MOVEIT_LIB_NAME moveit_lazy_free_space_updater)

add_library(${MOVEIT_LIB_NAME} SHARED src/lazy_free_space_updater.cpp)
set_target_properties(${MOVEIT_LIB_NAME} PROPERTIES VERSION "${${PROJECT_NAME}_VERSION}")
set_target_properties(${MOVEIT_LIB_NAME} PROPERTIES COMPILE_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
set_target_properties(${MOVEIT_LIB_NAME} PROPERTIES LINK_FLAGS "${OpenMP_CXX_FLAGS}")
ament_target_dependencies(${MOVEIT_LIB_NAME}
  rclcpp
  moveit_ros_occupancy_map_monitor
  Boost
  sensor_msgs
)

install(TARGETS ${MOVEIT_LIB_NAME}
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib
        RUNTIME DESTINATION bin)
install(DIRECTORY include/ DESTINATION include)
