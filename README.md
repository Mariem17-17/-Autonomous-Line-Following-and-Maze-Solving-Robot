# Autonomous Line-Following and Maze-Solving Robot

## Overview

This project is an Arduino-based autonomous robot designed to follow lines and solve mazes using a combination of infrared sensors, an MPU6050 accelerometer/gyroscope, ultrasonic sensors, and motor control. The robot uses Proportional-Integral-Derivative (PID) control to adjust its path and maintain smooth navigation while avoiding obstacles.

## Hardware Components

- **Arduino** (any compatible model)
- **MPU6050** (Accelerometer and Gyroscope)
- **Infrared Sensors** (IR for line detection)
- **Ultrasonic Sensor** (for obstacle detection)
- **DC Motors** (for movement)
- **LED** (for calibration indication)
- **Limit Switches** (for course control)
- **Power Supply and Wiring**

## Features

### 1. **Line Following**
The robot uses five infrared sensors to distinguish between black (line) and white (background) surfaces. During setup, these sensors are calibrated to detect threshold values for accurate line following.

### 2. **Maze Solving**
The robot utilizes a simple maze-solving algorithm, making decisions based on IR sensor data and ultrasonic sensor feedback to adjust its path through the maze.

### 3. **PID Control**
The MPU6050 provides accurate angle measurements, and a PID control system ensures the robot follows a straight path, even if it starts off misaligned.

### 4. **Obstacle Detection**
The ultrasonic sensor constantly measures distances to obstacles. When an object is detected too close, the robot adjusts its course or stops to avoid collisions.

## How It Works

1. **Sensor Calibration**: The robot calibrates its infrared sensors to differentiate between the black line and the white surface, storing the threshold values for optimal navigation.
  
2. **Line Following**: Using sensor data, the robot adjusts motor speeds to follow the line accurately. Different motor speeds ensure smooth turns and direction changes.

3. **Maze Navigation**: Upon entering a maze, the robot switches modes and begins solving the maze using its sensors to make decisions at each turn or intersection.

4. **Obstacle Avoidance**: The ultrasonic sensor ensures the robot avoids obstacles by measuring the distance to any objects in its path, prompting it to stop or reroute.

## Code Breakdown

- **Infrared Sensors**: Used to calibrate and detect line positions.
- **Motors**: Control the movement and turning of the robot.
- **Ultrasonic Sensor**: Used for obstacle detection and avoidance.
- **PID Control**: Maintains the robot’s direction and speed using data from the MPU6050.
- **Limit Switches**: Detect when the robot reaches the end of the course or a boundary.

## Setup Instructions

1. **Install Required Libraries**:
   - Ensure you have the `Wire.h` and `MPU6050_light.h` libraries installed in your Arduino IDE.
  
2. **Wiring**:
   - Connect the motors, IR sensors, MPU6050, and ultrasonic sensors as per the wiring diagram in the code. Ensure all components have proper power connections.
   
3. **Upload the Code**:
   - Upload the provided Arduino code to the robot.

## Calibration Process

1. Turn on the robot, which will enter the calibration phase with an LED indicator.
2. The robot will automatically calibrate the infrared sensors by scanning the black and white surfaces.
3. After calibration, the robot will begin line-following mode and can be placed on the track or maze.

## PID Tuning

The PID control constant `kp` can be adjusted to improve movement performance. A higher value results in quicker responses to misalignment, while a lower value produces smoother but slower corrections.

## Key Functions

- **seuilblack()** and **seuilwhite()**: Calculate the threshold values for black and white surfaces using the IR sensors.
- **forward_maze()**, **right_turn()**, **left_turn()**: Control robot movement while navigating the maze.
- **dour_pid()**: Adjusts the robot’s heading based on current angle readings from the MPU6050.
- **maze()**: The main maze-solving logic, adjusting movement based on sensor data.

## Usage

Once powered on, place the robot on a track or maze. The robot will autonomously follow the line, and upon detecting a maze, it will switch to maze-solving mode. The ultrasonic sensor ensures obstacle avoidance.

## Future Improvements

- **Dynamic Speed Optimization**: Adjusting speed based on track complexity.
- **Enhanced Maze Solving**: Implementing more advanced algorithms for complex mazes.
- **Improved Obstacle Avoidance**: Developing a more robust system for collision avoidance.

