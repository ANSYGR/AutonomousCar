README - 4-Wheeled Obstacle Avoidance Vehicle
This project is designed to control a 4-wheeled vehicle using an Arduino, equipped with an ultrasonic sensor (HCSR04), motor driver (L293DNE), and servos for steering. The vehicle can detect obstacles and navigate around them by adjusting its direction based on data from the ultrasonic sensor.

Table of Contents
Overview

Hardware Components

Libraries Used

Pin Configuration

Functions

Setup Instructions

Movement Logic

License

Overview
This project uses an Arduino to collect distance data from an HCSR04 ultrasonic sensor and control a 4-wheeled vehicle's movement. The vehicle will navigate around obstacles using the L293DNE motor controller, which drives two motors. The system scans the surrounding environment using a radar-like mechanism and makes decisions about which way to move (forward, left, or right).

Hardware Components
Arduino (e.g., Arduino Uno)

HCSR04 Ultrasonic Sensor (to detect obstacles)

L293DNE Motor Driver (to control the motors)

2 x Servo Motors (for steering and radar scanning)

4-Wheeled Chassis

Motors (2 for driving the vehicle)

Pin Configuration
The following pin assignments are used in this project:

Component	Pin
Trigger (HCSR04)	2
Echo (HCSR04)	3
Radar Servo	8
Steering Servo	11
Motor Pin 1	5
Motor Pin 2	6
Motor Pin 3	10
Motor Pin 4	9

Libraries Used
Servo.h: Controls the servo motors.

HCSR04.h: Interface for the HCSR04 ultrasonic distance sensor.

Functions
1. averageDistance(int samples)
This function averages distance measurements taken over a number of samples and filters out unrealistic values.

Returns the average distance.

2. scanRadar()
This function controls the radar servo to scan for obstacles at multiple angles (20°, 40°, 60°, 80°, 100°, 120°, 140°, and 160°).

Returns an array of distance measurements at each angle.

3. objIdent()
Identifies the direction of the closest obstacle by comparing the distance values from the scanRadar() function.

Returns the index corresponding to the direction of the closest obstacle.

4. Movement Functions
forward(): Moves the vehicle forward.

stopMotors(): Stops the vehicle by turning off both motors.

reverse(): Moves the vehicle in reverse.

checkReverse(): Checks if the vehicle is too close to an obstacle (less than 20 cm) and reverses the vehicle if necessary.

5. setup()
Initializes the sensor, motors, and servos, and starts serial communication.

6. loop()
Continuously checks the position of obstacles and makes movement decisions based on the proximity of obstacles.

If an obstacle is detected, the vehicle will steer left or right, depending on the position of the obstacle.

If there is no obstacle, the vehicle will move forward.

Setup Instructions
Connect the components to the Arduino according to the pin configuration table above.

Install the necessary libraries: Servo and HCSR04.

Upload the code to your Arduino using the Arduino IDE.

Ensure that your vehicle is placed in a suitable environment where it can safely move and detect obstacles.

Movement Logic
The vehicle uses the following logic to move around:

The radar servo scans the surroundings to detect obstacles.

The closest obstacle is identified using the objIdent() function.

The steering servo adjusts the direction based on the obstacle's position:

If no obstacle is detected, the vehicle moves forward.

If an obstacle is detected to the left, the vehicle turns left and moves forward.

If an obstacle is detected to the right, the vehicle turns right and moves forward.

If the vehicle is too close to an obstacle (less than 20 cm), it will reverse for 1 second before stopping and resuming its movements.

License
This project is open-source. Feel free to modify and use it for your own purposes. Please attribute the original work to the author: Andy Granfors.
