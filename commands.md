# Source and Build
source ~/ros2_ws/install/setup.bash
colcon build --symlink-install

# "View of the Finish Line"
ros2 launch neato2_gazebo neato_gauntlet_world.py
ros2 launch slam_toolbox online_sync_launch.py
ros2 service call /slam_toolbox/save_map slam_toolbox/srv/SaveMap "name:
  data: 'map_name'"
ros2 launch robot_localization test_amcl.py map_yaml:=path-to-your-yaml-file


# Running Your Own Particle Filter
ros2 launch robot_localization test_pf.py map_yaml:=path-to-your-yaml-file

