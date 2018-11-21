# turtlebot-walker-enpm808x
A project to implement Roomba  type walker behavior in turtlebot gazebo simulation 

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

A project to implement Roomba type walker behavior in turtlebot gazebo simulation.



## Dependencies

1. ROS Kinetic

2. System : Ubuntu 16.04

To install ROS, follow the instructions on this [link](http://wiki.ros.org/kinetic/Installation)

Don't forget to setup the ROS environment by adding the following line in your .bashrc :

```
$ source /opt/ros/kinetic/setup.bash

```
To install the turtlebot packages, run the following after installing ROS Kinetic on your ubuntu 16.04.

```
sudo apt-get install ros-kinetic-turtlebot-*

```
## Build Instructions 

Following the environment setup, next step is to create the workspace.

```
$ cd <path where workspace needs to be created>
$ mkdir -p <name of workspace>
$ cd <workspace>
<workspace>$ catkin_make

```
Now, for building 

```
<home>$ cd <workspace>/src
<workspace>/src$ git clone --recursive https://github.com/Indushekhar/turtlebot-walker-enpm808x
<workspace>/src$ cd ..
<workspace>$ catkin_make 

```

## Running the code using rosrun

Before starting the node, it is necessary to launch the world in gazebo. This can be done as follows:

```
<home>$ roslaunch turtlebot_gazebo turtlebot_world.launch

```

This will launch the turtlebot in gazebo.

Now, to run the walker node :

```
<home>$ rosrun turtlebot-walker-enpm808x walker

```

## Running the system using roslaunch

The Turtlebot simulation and walker node can also be launched by a launch file :

```
<home>$ roslaunch turtlebot-walker-enpm808x turtlebot_walker.launch 

```

To stop the simulation press CTRL+C in the same terminal.

## Recording bag files

The data publsihed during the simulation can be recoreded in a bag file using the launch file by running the following command:

```
<home>$ roslaunch turtlebot-walker-enpm808x turtlebot_walker.launch record:=true

```
This will record data for 30 secodns of all the topic except /camera/* topics.

We can check the information of the bag file using rosbag info command. Sample output looks like below:

```
indushekhar@indushekhar-GL502VMK:~/808X_ws/src/turtlebot-walker-enpm808x/results$ rosbag info walker.bag 

```

The output from above command is given below :

```

path:        walker.bag
version:     2.0
duration:    29.9s
start:       Dec 31 1969 19:00:00.29 (0.29)
end:         Dec 31 1969 19:00:30.15 (30.15)
size:        11.8 MB
messages:    23253
compression: none [16/16 chunks]
types:       bond/Status                           [eacc84bf5d65b6777d4c50f463dfb9c8]
             dynamic_reconfigure/Config            [958f16a05573709014982821e6822580]
             dynamic_reconfigure/ConfigDescription [757ce9d44ba8ddd801bb30bc456f946f]
             gazebo_msgs/LinkStates                [48c080191eb15c41858319b4d8a609c2]
             gazebo_msgs/ModelStates               [48c080191eb15c41858319b4d8a609c2]
             geometry_msgs/Twist                   [9f195f881246fdfa2798d1d3eebca84a]
             nav_msgs/Odometry                     [cd5e73d190d741a2f92e81eda573aca7]
             rosgraph_msgs/Clock                   [a9c97c1d230cfc112e270351a944ee47]
             rosgraph_msgs/Log                     [acffd30cd6b6de30f120938c17c593fb]
             sensor_msgs/Imu                       [6a62c6daae103f4ff57a132d6f95cec2]
             sensor_msgs/JointState                [3066dcd76a6cfaef579bd0f34173e9fd]
             sensor_msgs/LaserScan                 [90c7ef2dc6895d81024acba2ac42f369]
             std_msgs/String                       [992ce8a1687cec8c8bd883ec73ca41d1]
             tf2_msgs/TFMessage                    [94810edda583a504dfda3829e70d7eec]
topics:      /clock                                            2986 msgs    : rosgraph_msgs/Clock                  
             /cmd_vel_mux/active                                  1 msg     : std_msgs/String                      
             /cmd_vel_mux/input/navi                            298 msgs    : geometry_msgs/Twist                  
             /cmd_vel_mux/parameter_descriptions                  1 msg     : dynamic_reconfigure/ConfigDescription
             /cmd_vel_mux/parameter_updates                       1 msg     : dynamic_reconfigure/Config           
             /depthimage_to_laserscan/parameter_descriptions      1 msg     : dynamic_reconfigure/ConfigDescription
             /depthimage_to_laserscan/parameter_updates           1 msg     : dynamic_reconfigure/Config           
             /gazebo/link_states                               2967 msgs    : gazebo_msgs/LinkStates               
             /gazebo/model_states                              2967 msgs    : gazebo_msgs/ModelStates              
             /gazebo/parameter_descriptions                       1 msg     : dynamic_reconfigure/ConfigDescription
             /gazebo/parameter_updates                            1 msg     : dynamic_reconfigure/Config           
             /gazebo_gui/parameter_descriptions                   1 msg     : dynamic_reconfigure/ConfigDescription
             /gazebo_gui/parameter_updates                        1 msg     : dynamic_reconfigure/Config           
             /joint_states                                     2971 msgs    : sensor_msgs/JointState               
             /laserscan_nodelet_manager/bond                     56 msgs    : bond/Status                           (2 connections)
             /mobile_base/commands/velocity                     287 msgs    : geometry_msgs/Twist                  
             /mobile_base/sensors/imu_data                     2981 msgs    : sensor_msgs/Imu                      
             /mobile_base_nodelet_manager/bond                  112 msgs    : bond/Status                           (3 connections)
             /odom                                             2979 msgs    : nav_msgs/Odometry                    
             /rosout                                            327 msgs    : rosgraph_msgs/Log                     (9 connections)
             /rosout_agg                                        311 msgs    : rosgraph_msgs/Log                    
             /scan                                              276 msgs    : sensor_msgs/LaserScan                
             /tf                                               3725 msgs    : tf2_msgs/TFMessage                    (2 connections)
             /tf_static                                           1 msg     : tf2_msgs/TFMessage



```




## Playing back bag file

The saved bag file then can be played using following commands :

```
<home>$ cd <worskpace>/src/turtlebot-walker-enpm808x/results
<../results>$ rosbag play walker.bag

```

Running this will generate output like this :

```
[ INFO] [1542755215.360284072]: Opening walker.bag

Waiting 0.2 seconds after advertising topics... done.

Hit space to toggle paused, or 's' to step.
 [PAUSED ]  Bag Time:      6.180293   Duration: 5.900293 / 29.870000               55215.30 

```

You can now check on another terminal, which topics are being published by running :

```
<home>$ rostopic list

```
Once you have the list, you can see the topic message being publsihed by :

```
<home>$ rostopic echo <topic which needs to be checked>

```

### Note

Gazebo should not be running when playing bag file.




