# Obstacle Avoidance Robot

This project is an obstacle avoidance robot using an Arduino, Adafruit Motor Shield, Servo Motor, and Ultrasonic sensor. The robot moves forward and changes direction when it detects an obstacle.

## Components
- Arduino
- Adafruit Motor Shield
- 2 DC Motors
- Servo Motor
- Ultrasonic Sensor
- Power Supply

## Libraries
The following libraries are required:
- `AFMotor` for controlling the motors
- `Servo` for controlling the servo motor
- `NewPing` for interfacing with the ultrasonic sensor

## Pin Configuration
- Ultrasonic Sensor:
  - TRIG_PIN: A0
  - ECHO_PIN: A1
- Servo Motor: Pin 10

## Constants
- `MAX_DISTANCE`: Maximum sensor measuring distance (300 cm)
- `MAX_SPEED`: Maximum speed of the motors (160)
- `MAX_SPEED_OFFSET`: Speed offset for motor differences (40)
- `COLL_DIST`: Collision distance to stop and reverse (30 cm)
- `TURN_DIST`: Distance to veer away from object (50 cm)

## Setup
1. Attach the Adafruit Motor Shield to the Arduino.
2. Connect the DC motors to the Motor Shield.
3. Connect the Ultrasonic Sensor to pins A0 and A1.
4. Connect the Servo Motor to pin 10.
5. Install the required libraries in the Arduino IDE.

## Usage
1. Upload the `main.ino` file to the Arduino.
2. Power the robot.
3. The robot will move forward and change direction when it detects an obstacle.

## Functions
- `setup()`: Initializes the servo motor.
- `loop()`: Main loop to control the robot's movement.
- `changePath()`: Determines the new path when an obstacle is detected.
- `compareDistance()`: Compares distances to decide the direction.
- `readPing()`: Reads the distance from the ultrasonic sensor.
- `moveStop()`: Stops the motors.
- `moveForward()`: Moves the robot forward.
- `moveBackward()`: Moves the robot backward.
- `turnRight()`: Turns the robot to the right.
- `turnLeft()`: Turns the robot to the left.
- `turnAround()`: Turns the robot around.

## Additional Information
- The robot uses the `NewPing` library to measure distances using the ultrasonic sensor.
- The `AFMotor` library is used to control the DC motors via the Adafruit Motor Shield.
- The `Servo` library is used to control the servo motor for scanning the surroundings.

Thank you for giving your precious time to our project.