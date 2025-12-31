# Go2 Navigation and SLAM in Indoor Environments

This repository contains the simulation, perception, SLAM, and navigation setup developed for my Master's thesis:

**“Navigation and SLAM Design for a Quadruped Robot”**

The work focuses on a **Unitree Go2 quadruped robot**, simulated in **ROS 2 Jazzy** with **Gazebo Harmonic**, targeting indoor navigation and wall-inspection use cases.

---

## 📌 Project Scope

The main objectives of this project are:

- Simulation-first development using ROS 2 Jazzy and Gazebo Harmonic  
- Integration of a quadruped robot (Unitree Go2) with realistic sensors  
- LiDAR-based SLAM in indoor environments  
- Autonomous navigation using the ROS 2 Navigation (Nav2) stack  
- Reproducibility and clean software engineering practices suitable for academic work  

---

## 🧱 System Overview

The system currently includes:

- **Robot**: Unitree Go2 (simulated)
- **Simulation**: Gazebo Harmonic
- **Middleware**: ROS 2 Jazzy
- **Sensors**:
  - 2D LiDAR (LaserScan → `/scan`)
  - IMU
- **SLAM**: SLAM Toolbox
- **Visualization**: RViz2
- **Control**: ros2_control (joint effort controllers)

The project is developed and tested entirely in simulation before any real-world deployment.

---
## Current Status

✅ Gazebo Harmonic simulation running

✅ Go2 robot spawns upright in indoor environments

✅ LiDAR data available on /scan

✅ SLAM Toolbox publishing /map

✅ Indoor environment support

⬜ Robot locomotion via /cmd_vel (in progress)

⬜ Nav2 autonomous navigation (planned)

This repository represents a stable simulation baseline prior to enabling full locomotion and autonomous navigation behaviors.

## Requirements

The project is developed and tested using the following environment:

Ubuntu 24.04
ROS 2 Jazzy
Gazebo Harmonic
colcon
Python 3.12
Detailed installation and setup instructions will be provided as the project evolves.

## Future Work

Planned extensions of this work include:

Enabling reliable robot locomotion via /cmd_vel

Full Nav2 stack integration for autonomous navigation

Evaluation of indoor navigation and wall-inspection scenarios

Quantitative analysis of SLAM performance and map quality

Docker-based containerization for fully reproducible experiments

## Author

Florian Muanda
Master’s Student – AI for smart sensors and actuators/THD
GitHub: https://github.com/flo-77

## License

This project is intended for academic and research purposes.
All third-party software and dependencies retain their respective licenses.

## 📂 Repository Structure

```text
go2_ws/
├── src/
│   ├── unitree_go2_sim/          # Gazebo simulation and launch files
│   ├── unitree_go2_description/  # Robot description (URDF/Xacro, meshes)
│   ├── unitree_go2_nav/          # Navigation and SLAM configuration
│   └── unitree_go2_ros2/         # ROS 2 integration packages
├── build/                        # Colcon build artifacts (ignored)
├── install/                      # Colcon install space (ignored)
├── log/                          # ROS logs (ignored)
└── README.md







This project is intended for academic and research purposes.
