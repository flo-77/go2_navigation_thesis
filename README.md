Here is a **README.md that is copy-paste ready**.
You can paste it **directly as-is** into your GitHub repository.

---

```markdown
# go2_navigation_thesis

## Navigation and SLAM Design for a Quadruped Robot  
**Application: Indoor Wall Inspection**

This repository contains the simulation and navigation stack developed for a Master’s thesis focused on **SLAM and autonomous navigation for a quadruped robot (Unitree Go2)** in **indoor environments**, with a target application of **wall inspection**.

The project is based on **ROS 2 Jazzy** and **Gazebo (Gazebo Sim / Ignition)** and is designed to be **fully reproducible**, **offline**, and **hardware-agnostic**.

---

## ✨ Current Capabilities (Baseline)

✔ Go2 simulated in Gazebo  
✔ Custom **local warehouse environment** (offline, no Fuel dependency)  
✔ Stable robot spawn with correct physics  
✔ Locomotion via `/cmd_vel`  
✔ SLAM Toolbox integration (mapping verified)  
✔ Ready for Nav2 and perception extensions  

---

## 🏗 Repository Structure

```

go2_navigation_thesis/
├── src/
│   ├── unitree_go2_ros2/
│   │   └── unitree_go2_sim/
│   │       └── launch/
│   │           └── unitree_go2_launch.py
│   └── unitree_go2_description/
│       └── worlds/
│           └── warehouse_local.sdf

```

### Key components

- **`unitree_go2_sim`**  
  Launches Gazebo, spawns the Go2 robot, bridges ROS ↔ Gazebo, and supports loading a custom world via launch arguments.

- **`unitree_go2_description`**  
  Contains the robot description and a **fully local warehouse environment** (`warehouse_local.sdf`).

---

## 🧱 Warehouse Environment

The warehouse environment is defined locally in:

```

src/unitree_go2_description/worlds/warehouse_local.sdf

````

Features:
- Flat ground plane
- Four enclosing walls
- Three long shelf rows (obstacles)
- Fully offline (no Gazebo Fuel usage)

This environment is intentionally simple and structured, making it suitable for:
- SLAM evaluation
- Navigation benchmarking
- Wall-following and inspection tasks

---

## 🚀 How to Run (Fresh Machine / Native Ubuntu)

### 1️⃣ Clone and build

```bash
git clone https://github.com/flo-77/go2_navigation_thesis.git
cd go2_navigation_thesis

source /opt/ros/jazzy/setup.bash
rosdep install --from-paths src --ignore-src -r -y

colcon build --symlink-install
source install/setup.bash
````

### 2️⃣ Launch Go2 in the warehouse

```bash
ros2 launch unitree_go2_sim unitree_go2_launch.py \
  world:=src/unitree_go2_description/worlds/warehouse_local.sdf \
  world_init_x:=-8 \
  world_init_y:=-8 \
  world_init_z:=1.0
```

The robot will spawn **standing and stable** inside the warehouse.

### 3️⃣ Basic motion test

```bash
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist \
  "{linear: {x: 0.2}, angular: {z: 0.0}}" -r 10
```

---

## 🧭 SLAM

SLAM is performed using **SLAM Toolbox** in online asynchronous mode:

```bash
ros2 launch slam_toolbox online_async_launch.py use_sim_time:=true
```

The robot can rotate in place to build a consistent 2D occupancy map of the warehouse.

---

## 🔜 Next Steps (Planned)

### 1. SLAM Refinement

* Tune scan parameters and update rate
* Improve map quality near walls
* Save final occupancy maps for navigation

### 2. Nav2 Integration

* Configure robot footprint and costmaps
* Enable localization using the saved map
* Autonomous navigation inside the warehouse

### 3. Wall Inspection Camera

* Add an RGB or depth camera to the Go2 URDF
* Mount camera facing sideways or upward
* Publish camera topics (`/image_raw`)
* Use navigation + perception for wall-following inspection

### 4. Final Pipeline

```
Gazebo Warehouse
   ↓
Go2 + Sensors
   ↓
SLAM Toolbox
   ↓
Nav2 (Localization + Planning)
   ↓
Camera-based Wall Inspection
```

---

## 🎓 Thesis Context

This work supports a Master’s thesis titled:

**“Navigation and SLAM Design for a Quadruped Robot in Indoor Environments”**

with a practical focus on **autonomous wall inspection** using a legged platform.

---

## 🧠 Design Principles

* Offline worlds for reproducibility
* Quadruped platform with non-holonomic constraints
* Incremental development: SLAM → Nav2 → Perception
* Simulation-first, transferable to real Go2 hardware

---

## 📌 Notes

* The repository is intentionally minimal.
* External dependencies (Fuel, cloud assets) are avoided.
* The setup is validated in both virtualized and native Linux environments.

---


