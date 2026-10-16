
> Eye-in-hand grasping & sorting on a 6DOF vision robotic arm.
> Portfolio project for robotics / embodied-AI roles.

## What this is

Use the JetRover's end-effector HD camera + 3D depth camera to close the
perception-action loop: detect, estimate pose, plan, grasp, sort.

**First mission: marine plastic-bottle detection and pickup.** A direct sequel to my 2019 Drexel senior design (MEM-493, Group 32) — the "Automated River Cleaner," a catamaran boat robot with a TensorFlow bottle detector running on a Raspberry Pi. Recognition worked: 100 bottle-recognition tests at ~80% average confidence. But senior design ran out of time — the loop was never closed, and picking the bottles up stayed on a human with a remote control. Add the Pi's 1.2 FPS (too slow for a 1.5 m/s river, as our final report admits), and the mission was left unfinished. Seven years later: YOLO + TensorRT on a Jetson Orin NX at 30+ FPS, plus a 6DOF arm to finally close the grasp loop. Same river, new silicon.

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

## Project archive (2019)

The original senior design that started it all — Drexel MEM-493, Group 32 (team of 5; I was project manager):

- [Final report (PDF)](docs/MEM-493_Senior_Design_Final_Report.pdf) — full documentation: stakeholder needs, boat design & FEA, TensorFlow bottle detection on Raspberry Pi, test data, cost analysis
- [Final presentation slides (PDF)](docs/MEM493_Final_Presentation.pdf)
-  [Retrospective: 2019 → 2026](docs/RETROSPECTIVE.md) — honest look back: what worked, the gaps (1.2 FPS, the unclosed loop), and how each gap became a design decision in this project

