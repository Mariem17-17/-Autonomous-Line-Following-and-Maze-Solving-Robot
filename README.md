# Autonomous Line-Following and Maze-Solving Robot

## Overview

This project is an Arduino-based autonomous robot that follows a line and solves a maze using infrared sensors, an MPU6050 accelerometer/gyroscope, ultrasonic sensors, and motor control. The robot is capable of adjusting its direction using proportional-integral-derivative (PID) control to ensure smooth navigation while avoiding obstacles and completing a predefined path.

## Hardware Components

- **Arduino** (any compatible model)
- **MPU6050** (Accelerometer and Gyroscope)
- **Infrared Sensors** (IR)
- **Ultrasonic Sensor** (for distance measurement)
- **Motors** (DC motors for movement)
- **LED** (for calibration indication)
- **Fin de Course** (limit switches for course control)
- **Wires and Power Supply**

## Features

### 1. **Line Following**
The robot uses five infrared sensors to detect black and white colors, helping it to follow a line. These sensors are calibrated in the setup phase to determine the threshold values for detecting black and white surfaces.

### 2. **Maze Solving**
The robot implements a maze-solving algorithm. It makes turns based on sensor readings and distance data from the ultrasonic sensor, adjusting its path dynamically.

### 3. **PID Control**
The MPU6050 sensor is used for precise angle measurement, and the PID control algorithm ensures that the robot follows a straight path even when its initial direction is misaligned.

### 4. **Obstacle Detection**
The ultrasonic sensor measures the distance to obstacles in front of the robot. When an object is too close, the robot reacts accordingly by stopping or adjusting its path.

## How It Works

1. **Sensor Calibration**: The robot first calibrates its infrared sensors by measuring both black and white surfaces. It stores threshold values for each sensor, which are then used to differentiate between black (line) and white (background) surfaces.

2. **Line Following**: Based on the calibrated threshold values, the robot reads from the infrared sensors and adjusts its motors to stay on the line. The line-following logic makes use of different motor speeds to ensure smooth and accurate navigation.

3. **Maze Navigation**: When the robot encounters a maze, it switches to maze-solving mode, where it turns left, right, or moves forward based on sensor readings.

4. **Obstacle Avoidance**: The ultrasonic sensor continuously measures the distance to the nearest obstacle. If the robot detects an object too close, it stops or turns to avoid it.

## Code Breakdown

- **Infrared Sensors**: Calibrates the IR sensors and reads their values to guide the robot along the line.
  
- **Motors**: Controls the left and right motors independently to perform forward movement, left and right turns.

- **Ultrasonic Sensor**: Measures distance to obstacles and adjusts robot behavior accordingly.

- **PID Control**: Uses MPU6050 sensor data to adjust the robot's speed and maintain a straight path.

- **Limit Switches (Fin de Course)**: Detects when the robot reaches the end of the course or encounters a boundary, triggering actions to handle such scenarios.

## Setup

1. **Install Libraries**: Ensure that the MPU6050 library is installed in your Arduino IDE.
   - `Wire.h`
   - `MPU6050_light.h`

2. **Wiring**: 
   - Connect the motors, IR sensors, MPU6050, and ultrasonic sensors as specified in the code. Ensure proper power connections.
   
3. **Upload Code**: Upload the provided Arduino code to the robot.

## Calibration

1. Power on the robot, and ensure the LED is ON during the calibration phase.
2. The robot will automatically calibrate its infrared sensors for black and white surfaces.
3. After calibration, the robot will start line-following mode, and you can place it on the track or maze.

## PID Tuning

- The PID control constant `kp` can be adjusted to fine-tune the robot’s movement. A higher value will make the robot respond more aggressively to directional changes, while a lower value will result in smoother but slower corrections.

## Key Functions

- **seuilblack()** and **seuilwhite()**: Used for calculating the average black and white threshold values for the infrared sensors.
- **forward_maze()**, **right_turn()**, **left_turn()**: Control the movement of the robot when navigating the maze.
- **dour_pid()**: Uses the MPU6050 to adjust the robot’s heading based on its current angle.
- **maze()**: Main logic for solving a maze, making use of sensor readings to adjust the robot’s path dynamically.

## Usage

- Once the robot is powered on and placed on a track or maze, it will follow the line autonomously. If a maze is detected, it will switch to maze-solving mode.
- The robot will stop automatically if it detects an obstacle too close using the ultrasonic sensor.

## Future Improvements

- **Speed Optimization**: Adjusting the speed of the robot dynamically based on the complexity of the track.
- **Enhanced Maze Solving**: Implementing more advanced algorithms for solving complex mazes.
- **Obstacle Avoidance**: Integrating a more robust collision-avoidance system.

## License

This project is open-source and can be modified or distributed freely.#   A u t o n o m o u s - L i n e - F o l l o w i n g - a n d - M a z e - S o l v i n g - R o b o t  
 