# Vision-Guided Grasping with HiWonder JetRover

> Eye-in-hand grasping & sorting on a 6DOF vision robotic arm.
> Portfolio project for robotics / embodied-AI roles.

## What this is

Use the JetRover's end-effector HD camera + 3D depth camera to close the
perception-action loop: detect, estimate pose, plan, grasp, sort.
The classic "intelligent sorting" demo, built as a real engineering pipeline
instead of a vendor sample script.

## Hardware

- HiWonder JetRover Ultimate Kit (Jetson Orin NX Super 16GB, Mecanum chassis)
- 6DOF robotic arm, 35 kg serial bus servos, HD camera at end effector
- 3D depth camera + LiDAR (depth used for pose estimation)

## Pipeline

Camera stream to YOLO detection to depth-based 6D pose to arm motion planning
to grasp execution to place / sort by class.

## Roadmap

- R0 Bring-up: ROS 2 bring-up, camera calibration, arm teleop and joint limits
- R1 Perception: YOLO (TensorRT on Orin NX) + depth point-cloud pose estimation
- R2 Grasping loop: detection-to-grasp closed loop, success-rate benchmark
- R3 Sorting demo: multi-class sorting task + demo video

## Tech

ROS 2, YOLOv8, TensorRT, OpenCV, depth point clouds, Python

## Status

- Hardware on hand (JetRover Ultimate Kit)
- R0: ROS 2 bring-up and calibration — next
- R1: perception pipeline
- R2: grasping closed loop
- R3: sorting demo
