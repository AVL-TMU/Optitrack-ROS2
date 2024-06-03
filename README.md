# Optitrack-ROS2
Getting Optitrack running with ROS2
Original Source: https://github.com/MOCAP4ROS2-Project/mocap4ros2_optitrack

1. Git Clone this Repository Recursively "--recursive"
2. cd into mocap4r2_ws/src and verify mocap4r2 + mocap4ros2_optitrack + mocap_msg
3. do "cd .." and then "rosdep install --from-paths src --ignore-src -r -y"
4. do "cd into src" and then "vcs import < mocap4ros2_optitrack/dependency_repos.repos"
5. do "cd .." into Optitrack-ROS2/mocap4r2_ws
6. do "colcon build --symlink-install"
7. do "nano src/mocap4ros2_optitrack/mocap4r2_optitrack_driver/config/mocap4r2_optitrack_driver_params.yaml"
8. change [connection_type: "Unicast"] to [connection_type: "Multicast"]
9. Verify [server_address: "192.168.0.118"] with Optitrack Computer IP
10. Verify [local_address: "192.168.0.87"] with your Computer IP
11. Verify [multicast_address: "239.255.42.99"] with Optitrack Computer
12. Verify [server_command_port: 1510] with Optitrack Computer
13. Verify [server_data_port: 1511] with Optitrack Computer
14. Match [rigid_body_name: "insert_name_of_body"] with Optitrack Body Frame/Object
15. Save the file and make sure your in Optitrack-ROS2/mocap4r2_ws
16. do "colcon build --symlink-install" + "source install/local_setup.bash" + "source /opt/ros/your_ros_version/setup.bash"
17. do "ros2 launch mocap4r2_optitrack_driver optitrack2.launch.py" and make sure you dont get "driver not connected... :(" type of error but the "... conected!" along with other info lines
18. go to another terminal and do "ros2 lifecycle set /mocap4r2_optitrack_driver_node activate" to activate its node when needed
19. go to another terminal and do "ros2 launch mocap4r2_marker_viz mocap4r2_marker_viz.launch.py mocap4r2_system:=optitrack" and see if the body is displaying
 
