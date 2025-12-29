# Warehouse Robot Navigation using AWS Greengrass

## Overview
This project implements an autonomous warehouse robot navigation system. Robots navigate warehouse aisles while avoiding obstacles using sensor data. Models are trained in AWS SageMaker and deployed to edge devices using AWS Greengrass for real-time inference.

---

## Problem Statement
Autonomous robots in warehouses must navigate efficiently and safely. The goal is to use sensor data (LIDAR and ultrasonic sensors) to detect obstacles and optimize paths, reducing collisions and improving operational efficiency.

---

## Key Components

### Data
- LIDAR and Ultrasonic sensors (IoT)
- Dataset includes positional and sensor readings (`lidar_min`, `lidar_max`, `ultrasonic_left`, `ultrasonic_right`, `x`, `y`, `orientation`, `battery_level`, `collision_flag`, `path_smoothness`, `time_taken`)

### Model
- **Obstacle Detection**: Fully-connected neural network (`ObstacleDetector`) for predicting collisions
- **Path Optimization**: Deep Q-Network (DQN) reinforcement learning for selecting optimal actions

### Cloud
- AWS SageMaker for model training
- AWS Greengrass for edge deployment and inference

### Deployment
- Edge inference on robots for real-time collision detection and path optimization

### Monitoring
- Collision alerts triggered if `collision_flag` predicted
- Path smoothness and performance metrics monitored in real-time

---
## Architecture Diagram
Sensors (LIDAR / Ultrasonic)
↓
Edge Device with Greengrass
↓
ML Models
├── CNN / FC Network (Obstacle Detection)
└── DQN (Path Optimization)
↓
Robot Actuators
↓
Cloud Monitoring & Alerts
## Usage Instructions

1. **Install dependencies**:

```bash
pip install -r requirements.txt
2.Train the model in SageMaker (if needed) using src/model.py and src/dataset.py.

3.Run inference on edge device with Greengrass:
from src.inference import infer_collision
pred = infer_collision(state)
if pred == 1:
    send_alert({"alert": "Collision detected"})
4.Notebooks:

notebooks/warehouse robot.ipynb contains RL training and evaluation steps.
Status

✅ Completed – model trained, RL tested, and inference logic ready for edge deployment.
## Architecture Diagram

