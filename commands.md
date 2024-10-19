# Source and Build
source ~/ros2_ws/install/setup.bash
colcon build --symlink-install

# "View of the Finish Line"
ros2 launch neato2_gazebo neato_gauntlet_world.py

ros2 launch slam_toolbox online_sync_launch.py

---
# Rviz2
rviz2 -d ~/ros2_ws/src/robot_localization/rviz/turtlebot_bag_files.rviz

## Run your own bag
ros2 bag play robot_localization/maps/mac_1st_floor_final.yaml --clock 


## Teleop
ros2 run teleop_twist_keyboard teleop_twist_keyboard

*use i and , to move forward and backwards*

# Running Your Own Particle Filter
ros2 launch robot_localization test_pf.py map_yaml:=built_in_pf_map.yaml




# According to Ariel:

## MAC
Run rviz2 command
Map
Play a bag
record bag: ros2 bag record /accel /bump /odom /cmd_vel /scan /robot_description /stable_scan /projected_stable_scan /clock /tf /tf_static -o bag-file-name-here

Start running node
End bag


## Gauntlet
RVIZ
Gauntlet map
File
Teleop

### notes

change the spread and increase the size of your particles
from 300 to 10000
