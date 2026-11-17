#Warehouse Management using ROS 2

An autonomous warehouse simulation framework built with ROS 2, integrating SLAM (RTAB-Map), Nav2, and ArUco marker detection for automated inventory tracking and navigation using a simulated TortoiseBot in Gazebo.

📋 Table of Contents

Overview

Key Features

System Architecture & Methodology

Tech Stack

Packages Included

Installation & Build

Usage

Authors & Acknowledgments

📖 Overview

Modern warehouses require high speed, adaptability, and precision—areas where traditional manual operations often face bottlenecks, higher operational costs, and human error.

This project demonstrates a scalable, modular simulation of an Autonomous Mobile Robot (AMR) operating within a realistic Gazebo warehouse environment. Equipped with a camera and LiDAR, the simulated TortoiseBot maps its surroundings, localizes itself in real time, identifies pallets/shelves via ArUco markers, and autonomously navigates to target drop-off and pickup locations.

✨ Key Features

Autonomous Navigation: Utilizes the ROS 2 Navigation Stack (Nav2) for dynamic path planning and obstacle avoidance.

Real-Time Mapping & Localization: Implements SLAM (RTAB-Map) using onboard LiDAR and camera feeds to build and localize within the warehouse environment.

Vision-Based Object Detection: Integrates ros2_aruco and OpenCV to detect ArUco markers (DICT_5X5_250) representing pallets and shelf positions, estimating their 3D pose via tf2.

Modular Node Architecture: Built on ROS 2's distributed architecture, making the simulation easily extensible for multi-robot fleets or future physical hardware deployment.

🛠 System Architecture & Methodology

[ Gazebo Warehouse & TortoiseBot Setup ]
                   │
                   ▼
   [ Camera & LiDAR Sensor Integration ]
                   │
                   ▼
      [ SLAM Mapping (RTAB-Map) ]
                   │
                   ▼
 [ ArUco Marker Detection (ros2_aruco) ]
                   │
                   ▼
  [ Autonomous Navigation (ROS 2 Nav2) ]


💻 Tech Stack

Middleware: ROS 2

Simulation & Visualization: Gazebo, RViz2

Navigation & SLAM: Nav2, RTAB-Map, tf2

Computer Vision: OpenCV, ros2_aruco

Robot Platform: TortoiseBot (Differential drive with LiDAR & RGB Camera)

📦 Packages Included

Based on the workspace structure, this repository contains the following core ROS 2 packages:

pick_and_place: Handles high-level task execution and warehouse pickup/delivery logic.

ros2_aruco: ROS 2 wrapper for ArUco augmented reality marker detection and pose estimation.

ros2_aruco_interfaces: Custom message and service definitions for publishing marker poses and IDs.

🚀 Installation & Build

Prerequisites

Ubuntu Linux (22.04 recommended for ROS 2 Humble)

ROS 2 installed and sourced

Gazebo, RViz2, Navigation2, and RTAB-Map packages:

sudo apt update
sudo apt install ros-$ROS_DISTRO-navigation2 ros-$ROS_DISTRO-nav2-bringup ros-$ROS_DISTRO-rtabmap-ros


Clone & Build Workspace

Create a ROS 2 workspace and clone the repository:

mkdir -p ~/ros2_ws/src
cd ~/ros2_ws/src
git clone https://github.com/<your-username>/<your-repo-name>.git


Build the packages using colcon:

cd ~/ros2_ws
colcon build


Source the workspace:

source install/setup.bash


🎮 Usage

Launch the Gazebo Warehouse Environment:
(Update this command with your specific world/robot launch file)

ros2 launch <your_robot_pkg> warehouse_simulation.launch.py


Start ArUco Marker Detection:
Run the aruco_node specifying your marker size (e.g., 0.05 meters):

ros2 run ros2_aruco aruco_node --ros-args -p marker_size:=0.05


Subscribed Topics: /camera/image_raw, /camera/camera_info

Teleoperation (Optional - for initial manual mapping):

ros2 run teleop_twist_keyboard teleop_twist_keyboard


Run Pick and Place / Navigation Task:

ros2 run pick_and_place pick_and_place


🎓 Authors & Acknowledgments

Submitted in partial fulfillment of the requirement for the degree of Robotics and Automation (2022–2026)

Symbiosis Institute of Technology

Authors:

Samradny Ware

Poorna Singh

Namrata Todkar

Project Guide:

Dr. Manoj Shukla

📚 References

F. P. Audonnet, A. Hamilton, and G. Aragon-Camarasa, "A Systematic Comparison of Simulation Software for Robotic Arm Manipulation using ROS2," arXiv, 2022.

P. Padalkar et al., "Industrial Warehouse Robot Simulation Using ROS," Springer, 2023.

M. Z. Andreasen, P. I. Holler, and M. Albano, "MAES: A ROS2-Compatible Simulation Tool for Exploration and Coverage Algorithms," Springer, 2023.

Q. Pan, "Design and Analysis of an Autonomous Warehouse Robot System with 6-DOF Manipulator," EWA Direct - ACE Proceedings, 2024.

S. Borse et al., "A ROS2-based Navigation and Simulation Stack for the Robotino," arXiv, 2024.
