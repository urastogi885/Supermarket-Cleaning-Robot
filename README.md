# Supermarket Cleaning Robot
[![Build Status](https://travis-ci.org/urastogi885/supermarket-cleaning-robot.svg?branch=master)](https://travis-ci.org/urastogi885/supermarket-cleaning-robot)
[![License](https://img.shields.io/badge/License-MIT--Clause-blue.svg)](https://github.com/urastogi885/supermarket-cleaning-robot/blob/master/LICENSE)
---

## Overview

According to a study done in Morrisville, North Carolina, the Walmart Supercenter located in the town
receives about 10,000 people per day. Unquestionably, the actual foot traffic depends on a variety of
factors, but we cannot disregard that supermarkets are one of the busiest places in a town. The more the
number of people, the more likely it is for the store to become dirty. It always begets frustration among
workers to maintain the store at its most pristine level. Our supermarket cleaning robot can remove the
stress of cleanliness by performing the tasks of an employee.

Currently, most of the robots are only capable of executing a single task. It turns out to be expensive for
a store owner to buy a robot that can perform a single task. We propose to develop a robot that can
perform various maintenance tasks. The robot will be able to maintain cleanliness as well as make
supermarkets autonomous. The robot will able to clean aisles, stack up empty rows, and collect fallen
items.

For prototyping, we are focusing on only one task that is identifying and collecting the items using the
robot. The robot will roam in a supermarket like environment in Gazebo and identify the type of items
that it needs to collect. It identifies the item using a camera and HSV Color Detection algorithm, mounted on its base, and moves towards the
fallen item. Here, we are considering objects such as food, soft drinks cans and it is assumed that the robot
will already know the type of item that it needs to pick. As the robot reaches the location of the item and
touches it, the item will vanish depicting that the item is collected using a suction cup. The robot will
traverse randomly in the supermarket and keep on collecting a can. We are focusing on the detection of
cans using the OpenCV to improve the processing of the detection feature. In addition to this, the robot
has an obstacle avoidance feature that is used to prevent the robot from colliding from obstacles such as
humans, uninteresting items and walls/shelves.

<p align="center">
  <img src="https://github.com/urastogi885/supermarket-cleaning-robot/blob/master/data/readme_images/supermarket_world.jpg">
  <b>Figure 1 - Robot approaching towards the cans lying on the ground to collect them</b>
</p>


## Team Members

- [Umang Rastogi](https://github.com/urastogi885) - Pursuing masters in Robotics at University of Maryland | B.Tech in Electronics & Communication Engineering
- [Naman Gupta](https://github.com/namangupta98) - Grad Student at University of Maryland, pursuing M.Eng. in Robotics.

## Demo

In this demo, the turtlebot is our cleaner robot which traverses in the supermarket environment and keeps on scanning for the cans. As the can is detected, a bounding box is created and then the turtlebot apprached towards the can to collect it.

<p align="center">
  <img src="https://github.com/urastogi885/supermarket-cleaning-robot/blob/master/data/readme_images/demo.gif">
  <br><b>Figure 2 - Demo of Robot scanning and detecting items</b><br>
</p>

## Presentation

Click on the link to preview [presentation](https://docs.google.com/presentation/d/1KiABS_kfmvH2YfD9WYNnicjoehHe6gC2hseT8R00nM4/edit?usp=sharing)

## AIP and Sprint Documents

- Click on this [*link*](https://docs.google.com/spreadsheets/d/1k6e7rM7TTvE5w2fQ_wuSDY_giNWaVuCHeImB6D53lT4/edit?usp=sharing)
to access our AIP Google Sheet.
- Click on this [*link*](https://docs.google.com/document/d/1iQZUstgoCCvtSvlcv1_xpxGW6ntUbkOpcgMuvrSP_ms/edit?usp=sharing)
to access our Sprint notes document.

## Accessing the UML Diagrams

- Open the *UML* directory of the project.
- Access UML diagrams from *uml* sub-directory.

## API Documentations

- [Gazebo Population Tag](http://gazebosim.org/tutorials?tut=model_population&cat=build_world)
- [cv_bridge](http://wiki.ros.org/cv_bridge/Tutorials/UsingCvBridgeToConvertBetweenROSImagesAndOpenCVImages)
- [HSV Color Detection](https://docs.opencv.org/trunk/df/d9d/tutorial_py_colorspaces.html)

## Known Bugs and Issues

- Right now we are facing the object collection issue, where our idea is to remove the object from the world as the robot reached the object. 
- The Cola Can should be vanished representing that the object has been collected by the robot.
- We are working to solve this issue.

## Dependencies

- Ubuntu 16.04/18.04
- ROS Kinetic/Melodic
- Gazebo
- Turtlebot-3 Packages

## Install Dependences

- It is highly recommended that ROS Kinetic/Melodic is properly installed on your system before the use of this project.
- Follow the instructions on the [*ROS Kinetic install tutorial page*](http://wiki.ros.org/kinetic/Installation/Ubuntu) or the 
  [*ROS Melodic install tutorial page*](http://wiki.ros.org/melodic/Installation/Ubuntu) to install ***Full-Desktop Version*** of ROS Kinetic.
- The full-version would help you install *Gazebo* as well. If you have ROS Kinetic pre-installed on your machine, use
  the following [*link*](http://gazebosim.org/tutorials?tut=install_ubuntu&cat=install) to just install *Gazebo* on your
  machine.
- Ensure successful installation by running *Gazebo* via your terminal window:
```
gazebo
```
- An empty window of *Gazebo Simulator* should be launched.
- Create your ROS workspace by following instructions on the [*create ROS workspace tutortial page*](http://wiki.ros.org/catkin/Tutorials/create_a_workspace).
- Make sure that Turtlebot-3 packages have been installed on your machine using the following commands:
```
cd <ROS_WORKSPACE>/
source devel/setup.bash
export TURTLEBOT3_MODEL=burger
roslaunch turtlebot3_gazebo turtlebot3_world.launch
``` 
- A window of *Gazebo Simulator* with various items with a Turtlebot-3 burger robot should be launched.
- If an error pops up upon launching the Turtlebot-3 world, then install the necessary Turtlebot-3 packages:
```
cd <ROS_WORKSPACE>/
git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs
git clone https://github.com/ROBOTIS-GIT/turtlebot3
cd ../ && catkin_make
```

## Build

Switch to your *src* sub-directory of your ROS workspace to clone this repository.
```
<ROS Workspace>/src
```
- Run the following commands to clone and build this project:
```
git clone --recursive https://github.com/urastogi885/supermarket-cleaning-robot
cd ../
catkin_make
```

## Test

Close and terminate everything including rosmaster. In a new terminal, switch to the ROS workspace and build the tests.  Type

```
cd catkin_ws
source devel/setup.bash
catkin_make run_tests_supermarket_cleaning_robot
```

## Run

Now, we use launch file to run. In a new terminal, type

```
cd catkin_ws
source devel/setup.bash
roslaunch supermarket_cleaning_robot object_collection.launch
```

## Doxygen

To install doxygen run the following command:

```
sudo apt-get install doxygen
```
Now from the cloned directory run:

```
doxygen Doxyfile
```

Generated doxygen files are in html format and you can find them in ./docs folder. With the following command

```
firefox docs/html/index.html
```
