# Vision-Guided Grasping with HiWonder JetRover

> Eye-in-hand grasping & sorting on a 6DOF vision robotic arm.
> Portfolio project for robotics / embodied-AI roles.

## What this is

Use the JetRover's end-effector HD camera + 3D depth camera to close the
perception-action loop: detect, estimate pose, plan, grasp, sort.

**First mission: marine plastic-bottle detection and pickup.** A continuation
of my 2019 senior design (TensorFlow CNN bottle recognition, 95% precision) —
this time with modern YOLO + TensorRT on Jetson, trained for the marine
environment (floating bottles, water glare, waves), ending with the arm
physically picking bottles up. Ocean-plastic cleanup: tech for good,
and a story only I can tell.

## Hardware

- HiWonder JetRover Ultimate Kit (Jetson Orin NX Super 16GB, Mecanum chassis)
- 6DOF robotic arm, 35 kg serial bus servos, HD camera at end effector
- 3D depth camera + LiDAR (depth used for pose estimation)

## Pipeline

Camera stream to YOLO detection to depth-based 6D pose to arm motion planning
to grasp execution to place / sort by class.

## Dataset (bottle detection)

- TACO (Trash Annotations in Context): in-the-wild trash incl. plastic bottles
- Roboflow Universe: ready-made YOLO-format bottle detection datasets
- JAMSTEC marine debris dataset
- Self-collected: photos of floating bottles on water (phone camera) — the key
  marine-specific data: reflections, waves, half-submerged bottles

## Roadmap

- R0 Bring-up: ROS 2 bring-up, camera calibration, arm teleop and joint limits
- R1 Perception: bottle dataset assembly, YOLOv8/YOLO11 training, TensorRT export, deploy on Orin NX
- R2 Grasping loop: detection-to-grasp closed loop on bottles, success-rate benchmark
- R3 Demo: multi-class sorting + demo video, marine-environment field test

## Tech

ROS 2, YOLOv8/YOLO11, TensorRT, OpenCV, depth point clouds, Python

## Status

- Hardware on hand; mission defined (marine bottle pickup)
- R0: ROS 2 bring-up and calibration — next
- R1: bottle dataset + YOLO training
- R2: grasping closed loop on bottles
- R3: demo and field test
