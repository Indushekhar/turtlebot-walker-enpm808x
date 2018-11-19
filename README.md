# turtlebot-walker-enpm808x
A project to implement Roomba  type walker behavior in turtlebot gazebo simulation 

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

##Overview

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
