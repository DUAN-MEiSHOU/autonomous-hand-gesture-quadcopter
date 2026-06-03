# Autonomous Hand Gesture Quadcopter

## Project Vision

Build a fully embedded, offline-capable DIY micro quadcopter that performs onboard hand gesture recognition and autonomous flight control.

The final system must NOT depend on:

- cloud services
- internet connection
- external computer
- remote inference

All perception, decision making, and control should run onboard the aircraft.

---

## Project Goal

Develop a self-contained UAV system capable of:

1. Capturing images using onboard camera
2. Detecting and tracking human hands
3. Recognizing predefined gestures
4. Mapping gestures to flight commands
5. Executing commands through flight controller
6. Operating completely offline

---

## Development Philosophy

This project is intended to demonstrate skills across:

- Computer Vision
- Embedded Systems
- UAV Systems
- Robotics
- Control Algorithms
- Edge AI

The project should prioritize engineering quality over rapid feature expansion.

Priority:

1. Reliability
2. Safety
3. Modularity
4. Real-time performance
5. Advanced features

---

# Hardware Architecture

## Aircraft

DIY Micro Quadcopter

Target size:

- 3 inch
or
- 3.5 inch

---

## Flight Controller

Current target:

- SpeedyBee F405

Possible alternatives:

- Matek F405

Firmware:

- Betaflight

Possible future migration:

- PX4
- ArduPilot

---

## Compute Module

Development Stage:

- Laptop + USB Camera

Deployment Stage:

- Raspberry Pi Zero 2W
or
- Raspberry Pi 4

Future options:

- Jetson Nano
- Jetson Orin Nano

---

## Camera

Development:

- USB Webcam

Deployment:

- Onboard Camera Module

---

# Software Architecture

Overall pipeline:

Camera
↓
Hand Detection
↓
Gesture Recognition
↓
Temporal Filtering
↓
Command Mapping
↓
Flight Control Interface
↓
Flight Controller
↓
Drone Motion

---

# Functional Modules

## vision/

Responsibilities:

- camera capture
- frame preprocessing
- hand detection
- landmark extraction

Preferred libraries:

- OpenCV
- MediaPipe

---

## gesture/

Responsibilities:

- gesture classification
- confidence estimation
- temporal filtering
- debounce logic

Output:

stable gesture label

---

## control/

Responsibilities:

- gesture-to-command mapping
- state machine
- command smoothing
- safety constraints

---

## communication/

Responsibilities:

- serial communication
- UART interface
- MSP protocol support

---

## onboard/

Responsibilities:

- deployment
- startup scripts
- hardware integration

---

# Supported Gestures

Initial gesture set:

- Open Palm
- Fist
- Point Left
- Point Right
- Thumb Up
- Thumb Down

Future gestures may be added later.

---

# Flight Commands

Initial command set:

- ARM
- DISARM
- TAKEOFF
- LAND
- MOVE_LEFT
- MOVE_RIGHT
- ASCEND
- DESCEND

---

# Control Algorithm Roadmap

## Phase 1

Gesture Recognition MVP

Goal:

Detect and classify gestures reliably.

---

## Phase 2

Command Mapping

Goal:

Convert gestures into flight commands.

---

## Phase 3

Flight Controller Integration

Goal:

Send commands to actual hardware.

---

## Phase 4

Control Optimization

Research topics:

- PID tuning
- command smoothing
- anti-trigger logic
- response stabilization

---

## Phase 5

Visual Servoing

Goal:

Drone follows user's hand position.

Pipeline:

Hand Position
↓
Position Error
↓
Control Correction
↓
Drone Motion

---

# Coding Standards

## General Rules

- Python first
- Modular design
- Clear comments
- Easy debugging
- Reusable functions

---

## Code Style

Preferred:

- Small files
- Small functions
- Single responsibility principle

Avoid:

- Large monolithic scripts
- Hardcoded constants
- Deep nesting

---

## Documentation

Every major module should include:

- purpose
- inputs
- outputs
- usage examples

---

# Git Workflow

Commit frequently.

Recommended milestones:

- init project
- webcam module
- hand detection
- gesture recognition
- temporal filtering
- command mapping
- UART communication
- onboard deployment
- first successful flight

---

# Safety Rules

Never generate code that:

- automatically spins motors on startup
- arms the drone without explicit user action
- bypasses safety checks

Always require confirmation before:

- arming
- takeoff
- autonomous movement

---

# Current Status

Current phase:

Project Planning

No implementation completed.

---

# Immediate Task

Build MVP Phase 1.

Requirements:

- Open webcam
- Detect hand landmarks
- Recognize basic gestures
- Display gesture label
- Display FPS

Expected result:

Real-time gesture recognition demo running on laptop.