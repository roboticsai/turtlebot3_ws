This repository contains ros modules which can be used to test the slam and navigation stack of ROS1. Turtlebot robots are developed for academic and research purpose. 
![Image of Yaktocat](https://github.com/roboticsai/turtlebot3_ws/blob/master/Docs/Images/48-turtlebotsJPG.jpg)

Requirments:
1. Ubuntu 18.04
2. ROS melodic desktop full installed

To build this modules:
1. Clone and build the hole workspace
   git clone https://github.com/roboticsai/turtlebot3_ws.git
2. Build with catkin_make
   cd turtlebot3_ws
   catkin_make
3. Source the workspace
   source devel/setup.bash
To run the different nodes follow below instructions:   
1. Choose which robot you want to use, options are burger, waffle and waffle pi. For this put this line in .bashrc file:
export TURTLEBOT3_MODEL=burger
2. To launch the turtlebot3 in gazebo:
   2.1. To launch in emptry world:
        roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
   2.2. To launch in its default world:
        roslaunch turtlebot3_gazebo turtlebot3_world.launch
   2.3. To launch in a house:
        roslaunch turtlebot3_gazebo turtlebot3_house.launch
3. To control the turtlebot3 with keyboard:
   roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
4. To let the turtlebot3 move autonomously in world:
   roslaunch turtlebot3_gazebo turtlebot3_simulation.launch
5. To run the slam node, options are gmapping and hector:
   roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
6. To save the final static map created by slam:
   rosrun map_server map_saver map:="/map-topic"    
7. To run the navigation stack of ros i.e move base:
   roslaunch turtlebot3_navigation turtlebot3_navigation.launch

After we have launched the navigation stack, initially the robot has to localize itself in the map. For that manually we can do this:
1. In rviz click 2d pose estimation and click in the correct location of turtlebot3   real world location in map. Also drag the arrow head to direction of turtlebot3 face.
![Image of Yaktocat](https://github.com/roboticsai/turtlebot3_ws/blob/master/Docs/Images/2d_pose_estimate.png)
2. Than move the robot with teleop key node. 
After this we can click any location in map and turtlebot3 will go their itself.

This repo used robot_localization ekf node for location purpose.
![Image of Yaktocat](https://github.com/roboticsai/turtlebot3_ws/blob/master/Docs/Images/rosgraph.png)
References: 
1. https://emanual.robotis.com/docs/en/platform/turtlebot3/navigation/#ros-1-navigation
2. https://automaticaddison.com/how-to-launch-the-turtlebot3-simulation-with-ros/
