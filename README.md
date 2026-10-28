Autonomous Navigation with TurtleBot3 and Nav2 in Gazebo
=======================================================

Repository: `antro-pi-robotics-turtlebot3-nav2`

An autonomous navigation and obstacle avoidance system for a TurtleBot3 robot, simulated in Gazebo Classic using ROS 2 Humble and Navigation2 (Nav2). The system integrates AMCL-based probabilistic localization, global and local costmaps, and the DWB local planner for trajectory generation and navigation.

Demo
----

Video: [Watch the demonstration on Google Drive](https://drive.google.com/file/d/1XyobtNhmrbenWuMGSZzdQ4K-q3GH2SOS/view?usp=sharing)

The video shows the robot in Gazebo and the navigation visualization in RViz2, including global path planning, AMCL localization, and dynamic obstacle avoidance.

Table of Contents
-----------------

1. [Overview](#1-overview)
2. [Key Features](#2-key-features)
3. [Technology Stack](#3-technology-stack)
4. [System Requirements](#4-system-requirements)
5. [Installation](#5-installation)
6. [Usage](#6-usage)
7. [Verification Checklist](#7-verification-checklist)
8. [Troubleshooting](#8-troubleshooting)

---

1. Overview
-----------

This project implements an autonomous navigation system for a TurtleBot3 robot in a Gazebo simulation environment. It uses ROS 2 Navigation2 (Nav2) for path planning and navigation, AMCL for localization, and costmaps for obstacle-aware navigation.

The project also demonstrates navigation in the presence of obstacles, as shown in the demonstration video.

2. Key Features
---------------

- Autonomous robot navigation using ROS 2 Nav2
- AMCL-based probabilistic localization
- Global and local costmaps
- Global path planning and DWB local trajectory planning
- Laser scan visualization in RViz2
- Gazebo Classic simulation
- Dynamic obstacle avoidance demonstrated in the project video

3. Technology Stack
-------------------

| Capability | Technology |
|---|---|
| Operating System | Ubuntu 22.04 LTS |
| Robotics Middleware | ROS 2 Humble Hawksbill |
| Simulation | Gazebo Classic (Gazebo 11) |
| Navigation | Navigation2 (Nav2) |
| Localization | AMCL |
| Global Planning | Nav2 Planner Server |
| Local Planning | DWB Local Planner |
| Visualization | RViz2 |
| Robot Platform | TurtleBot3 |

4. System Requirements
----------------------

- Ubuntu 22.04 LTS
- ROS 2 Humble Hawksbill
- Gazebo Classic
- TurtleBot3 packages
- Navigation2 packages
- RViz2

5. Installation
---------------

Step 1: Update Packages

```bash
sudo apt update
```

Step 2: Install Required ROS 2 Packages

```bash
sudo apt install -y \
  ros-humble-turtlebot3 \
  ros-humble-turtlebot3-gazebo \
  ros-humble-turtlebot3-simulations \
  ros-humble-navigation2 \
  ros-humble-nav2-bringup
```

Step 3: Configure the Environment

Add the following lines to your `~/.bashrc` file:

```bash
source /opt/ros/humble/setup.bash
export TURTLEBOT3_MODEL=burger
```

Apply the changes:

```bash
source ~/.bashrc
```

Note: Ensure that `TURTLEBOT3_MODEL` matches the robot model used by your simulation. Verify that the configured model matches the model spawned by your launch file.

6. Usage
--------

Step 1: Launch the Simulation

```bash
ros2 launch nav2_bringup tb3_simulation_launch.py headless:=False
```

This launch file starts the simulation and the associated Nav2 navigation stack.

Step 2: Set the Initial Pose

In RViz2:

1. Select 2D Pose Estimate.
2. Click the robot's actual location on the map.
3. Drag to indicate its heading.
4. Allow AMCL to converge and update the particle cloud.

Step 3: Send a Navigation Goal

1. Select Nav2 Goal in RViz2.
2. Click the desired destination on the map.
3. Drag to set the target orientation.
4. Observe the planned path and the robot's movement toward the goal.

Step 4: Demonstrate Dynamic Obstacle Avoidance

1. Start navigation toward a goal.
2. Introduce an obstacle into the robot's path in Gazebo.
3. Observe the sensor readings and the local costmap.
4. Observe how the robot responds to the obstacle and adjusts its path.

7. Verification Checklist
-------------------------

- [ ] Gazebo launches successfully.
- [ ] The intended TurtleBot3 model appears in the simulation.
- [ ] RViz2 displays the map, robot model, and laser scan.
- [ ] The initial pose is set and AMCL localization converges.
- [ ] A global path is generated after setting a navigation goal.
- [ ] The robot moves toward the goal.
- [ ] Dynamic obstacle avoidance is demonstrated in the video.

8. Troubleshooting
------------------

| Issue | Suggested Check |
|---|---|
| Robot model does not appear correctly | Verify the selected `TURTLEBOT3_MODEL` and confirm that `ros-humble-turtlebot3-gazebo` is installed. |
| Gazebo fails to launch | Check the terminal output. If a previous Gazebo process is stuck, terminate it before relaunching. |
| Map or costmaps do not appear | Check Nav2 node status and wait for the lifecycle nodes to become active. |
| Robot does not move toward the goal | Verify localization, navigation status, and that the laser scan topic is publishing. |
| RViz2 displays a missing model or mesh | Check whether the referenced model file and its ROS package are installed and available. |
