# Ai-robotics-week-5-tasks
Task 4: Using Turtlebot3 with SLAM for mapping

![00](https://user-images.githubusercontent.com/101488769/183163488-bc7b9d45-897b-4728-9eeb-0e712f8fd050.gif)
<br/>

## Table of Contents:-
* [1- Download and Install Ubuntu on PC](#1-Download-and-Install-Ubuntu-on-PC)
* [2- Install ROS on Remote PC](#2-Install-ROS-on-Remote-PC)
* [3- Install Dependent ROS Packages](#3-Install-Dependent-ROS-Packages)
* [4- Install TurtleBot3 Packages](#4-Install-TurtleBot3-Packages)
* [5- Gazebo Simulation](#5-Gazebo-Simulation)
* [6- SLAM Simulation](#6-SLAM-Simulation)
* [7- Testing](#7-Testing)
 <br/>

## 1-Download-and-Install-Ubuntu-on-PC:
### 1.1 Download the proper `Ubuntu 20.04 LTS Desktop` image for your PC from the links below.
* [Ubuntu 20.04 LTS Desktop image (64-bit)](https://releases.ubuntu.com/20.04/)
### 1.2 Follow the instruction below to install Ubuntu on PC:
* [Install Ubuntu desktop](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)
 <br/>

## 2-Install-ROS-on-Remote-PC:
Open the terminal with `Ctrl` + `Alt` + `T` and enter below commands one at a time.<br/>
In order to check the details of the easy installation script.<br/>
`$ sudo apt update` <br/>
`$ sudo apt upgrade` <br/>
`$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_noetic.sh` <br/>
`$ chmod 755 ./install_ros_noetic.sh`<br/>
`$ bash ./install_ros_noetic.sh`<br/>
<br/>

## 3-Install-Dependent-ROS-Packages:
`$ sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \`<br/>
  `ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \`<br/>
  `ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \`<br/>
  `ros-noetic-rosserial-python ros-noetic-rosserial-client \`<br/>
  `ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \`<br/>
  `ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \`<br/>
  `ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \`<br/>
  `ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-marker`<br/>
<br/>  

## 4-Install-TurtleBot3-Packages:
Install TurtleBot3 via Debian Packages.<br/>
`$ sudo apt install ros-noetic-dynamixel-sdk`<br/>
`$ sudo apt install ros-noetic-turtlebot3-msgs`<br/>
`$ sudo apt install ros-noetic-turtlebot3`<br/>
<br/>

## 5-Gazebo-Simulation:
### 5.1 Install Simulation Package:
The <b>TurtleBot3 Simulation Package</b> requires `turtlebot3` and `turtlebot3_msgs` packages as prerequisite. Without these prerequisite packages, the Simulation cannot be launched.<br/>
Please follow the [PC Setup](https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/) instructions if you did not install required packages and dependent packages<br/>

`$ cd ~/catkin_ws/src/` <br/>
`$ git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git`<br/>
`$ cd ~/catkin_ws && catkin_make`<br/>

### 5.2 Launch Simulation World:
Three simulation environments are prepared for TurtleBot3. Please select one of these environments to launch Gazebo.

<b>`Please make sure to completely terminate other Simulation world before launching a new world.`</b> <br/>
<b> TurtleBot3 World </b> <br/>

`$ export TURTLEBOT3_MODEL=waffle`<br/>
`$ roslaunch turtlebot3_gazebo turtlebot3_world.launch`<br/>
<br/>

![001](https://user-images.githubusercontent.com/101488769/183253606-f2ffca27-dc14-4280-abe4-5d2ec396f8df.png)
<br/>

## 6-SLAM-Simulation:
### 6.1 Run SLAM Node:
Open a new terminal from Remote PC with `Ctrl` + `Alt` + `T` and run the SLAM node. Gmapping SLAM method is used by default.<br/>
Please use the proper keyword among `burger` , `waffle` , `waffle_pi` for the TURTLEBOT3_MODEL parameter.<br/>

`$ export TURTLEBOT3_MODEL=burger`<br/>
`$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping`<br/>
<br/>

![002](https://user-images.githubusercontent.com/101488769/183254106-e2e0ef6f-f6f8-42e7-beb1-20b2c2385492.png)
<br/>

### 6.2 Run Teleoperation Node:
Open a new terminal from Remote PC with `Ctrl` + `Alt` + `T` and run the teleoperation node from the Remote PC.<br/><br/>
Please use the proper keyword among `burger` , `waffle` , `waffle_pi` for the TURTLEBOT3_MODEL parameter.<br/>

`$ export TURTLEBOT3_MODEL=burger`<br/>
`$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch`<br/>
<br/>

![03](https://user-images.githubusercontent.com/101488769/183254268-c071018e-238d-4295-a0da-a13191d9e55c.png)
<br/>

### 6.3 Save Map:
When the map is created successfully, open a new terminal from Remote PC with `Ctrl` + `Alt` + `T` and save the map. <br/>
<br/>

![003](https://user-images.githubusercontent.com/101488769/183255299-8d419137-7d54-4c37-ad62-7e5254e7df5b.png)
<br/>

`$ rosrun map_server map_saver -f ~/map` <br/>
<br/>

![04](https://user-images.githubusercontent.com/101488769/183255327-173fc3d4-b58b-42dd-acbb-0404b17f9647.jpg)
<br/>

## 7-Testing:
![Task 04 1](https://user-images.githubusercontent.com/101488769/183255856-863117a0-75c7-4983-bead-2f2e901e689b.gif)
