Engineering Documentation | Team Aitchison X | Pakistan
====

This repository contains information regarding a self-driven vehicle's model participating in the WRO Future Engineers competition in the season 2024.

Team Members:

Zarar Haroon - email: zararharoon@gmail.com

Ayaan Waqar - email: ayaanwaqar1@gmail.com

Zain Haroon - email: zainharoonkhokhar@gmail.com

## Content

* `t-photos` contains 2 photos of the team (an official one and one funny photo with all team members)
* `v-photos` contains 6 photos of the vehicle (from every side, from top and bottom)
* `video` contains the video.md file with the link to a video where driving demonstration exists
* `schemes` contains one or several schematic diagrams.
* `src` contains code of control software for all components which were programmed to participate in the competition
* `models` is for the attachments created as ad ons to the chasis.
* `other` is for other files which can be used to understand how to prepare the vehicle for the competition. 

## Introduction

## Build of Robot

## Chassis Features

4WD with Steering Axle: The chassis includes four-wheel drive and a steering axle, allowing it to behave like a normal car.

Metal Geared Motors: Equipped with durable metal geared motors for reliable performance.

Mounting Holes: Drilled holes for mounting Arduino, motor shields, and other components.

Bumper: Provides protection to the chassis and components.

## Creating Space for Components

On top of our chassis, we have strategically used metal studs to create a multi-tiered structure, allowing for an organized and efficient arrangement of components.
The first tier houses the Lipo Battery and the Motor Driver L298N. This level is crucial as it supports the main power supply and motor control system, ensuring easy access and stability.

The second tier is dedicated to three lithium-ion cells. These cells provide additional power, supplementing the Lipo Battery to ensure that the vehicle has sufficient energy for extended operation.

The third tier features a veroboard, which plays a vital role in wire management. The veroboard helps in organizing the myriad of wires, preventing tangling and ensuring a clean setup. On this level, we have mounted the Arduino Mega, which serves as the brain of our vehicle, and the Pixy camera, essential for visual processing and navigation.
At the very top, we have placed one buck-boost converter and one simple buck converter. These converters are essential for regulating the voltage supplied to various components, ensuring that each part receives the correct voltage for optimal performance.

To accommodate various sensors, we have employed Meccano pieces and plastic components, drilling precise holes into the chassis to create custom fittings. This meticulous setup ensures that all sensors are securely mounted and properly aligned for accurate data collection and functionality.

Overall, our multi-level design not only enhances the organization and accessibility of components but also contributes to the overall efficiency and performance of the vehicle. Each level is thoughtfully arranged to maximize functionality and maintain a clean, well-managed system.


## Mobility Management

Motor selection is a crucial component of our vehicle's autonomous navigation system. In making our selection, we considered key factors such as rotation speed, torque, efficiency, reliability and what it's used for.

![Capture](https://github.com/Zarar-Haroon/Aitchison-X---WRO-2024-/assets/170884737/d78ad5ae-82fa-41b9-8d11-67f2680d87b1)

We have designed our vehicle using two types of motors to ensure optimal performance.

Firstly, we employ a DC motor to drive the chassis. This motor is connected to a gear system and an axle, which collectively work to rotate both rear wheels simultaneously, thereby making our vehicle a rear-wheel drive. The connection to a motor driver allows us to meticulously control the DC motor's functions, including direction and speed. This ensures smooth and precise movement of the vehicle.

Secondly, we incorporate a servo motor dedicated to steering the car. The reliability and efficiency of this servo motor are paramount, as it is crucial for navigating the vehicle through various terrains and obstacles within the arena. The precision offered by the servo motor ensures that our vehicle can make sharp and accurate turns as required.
In addition to the motor setup, our vehicle boasts a robust and stable chassis. The design of the chassis is meticulously crafted to maintain the vehicle's balance at all times, preventing tipping or instability during operation. This stability is essential for maintaining control and ensuring the vehicle performs consistently under different conditions.
Overall, the combination of a powerful DC motor for propulsion, a precise servo motor for steering, and a sturdy chassis for balance, makes our vehicle well-equipped for navigating and performing efficiently in the arena.

## Power and Sense Management

We have incorporated a total of five ultrasonic sensors in our vehicle design: four standard ultrasonic sensors and one waterproof ultrasonic sensor. These sensors are integral to our navigation system, enabling the vehicle to maneuver through the arena efficiently while avoiding walls and obstacles. The sensors continuously measure distances to nearby objects, allowing the vehicle to keep track of the number of laps completed and to determine the direction in which to turn. By monitoring critical distances on the left and right sides, the sensors help avoid collisions and decide the optimal turning direction based on comparative distance data.

Additionally, we have equipped the vehicle with a Pixy camera to enhance obstacle detection and navigation. The Pixy camera is adept at identifying obstacles and determining their colors, which is crucial for deciding the side to which the vehicle should move. The compact size of the Pixy camera makes it an ideal fit for our chassis, and its ease of calibration and use made it the obvious choice for our design. By working in tandem with the ultrasonic sensors, the Pixy camera ensures the vehicle avoids collisions with walls and navigates effectively based on color cues from obstacles.

For powering the robot, we utilize a combination of a Lipo battery and three lithium-ion cells, connected to two buck converters—one of which includes a booster. The Lipo battery is connected to the buck-boost converter, which in turn is connected to the motor driver. This setup powers the DC motor and the Arduino Mega. The lithium-ion cells are connected to the standard buck converter, which supplies power to the sensors, Pixy camera, and servo motor. This configuration ensures that all components receive the precise amount of power they need to function correctly.

Specifically, the Arduino Mega requires a stable 5V power supply, so the output of the buck converter is set to 5V, with an input of 11.1V. Meanwhile, the buck-boost converter output is set to 12V, which is necessary as the DC motors require a minimum of 10V to operate efficiently. This careful power distribution guarantees that each component performs optimally, contributing to the overall reliability and effectiveness of our vehicle's navigation and operation systems.

## Obstacle Management

In the open round, our robot utilizes five ultrasonic sensors strategically placed to navigate and avoid obstacles. The sensors are positioned as follows:

One sensor at the front of the vehicle.

Two sensors positioned at 90-degree angles (left and right).

Two sensors positioned at 45-degree angles (left-front and right-front).

The operation begins with the robot moving straight. As it advances, the front sensor continuously measures the distance to any obstacles ahead. When the distance measured by the front sensor falls below a predetermined threshold, indicating the presence of an obstacle directly in front, the robot needs to turn.

At this point, the values from the two 90-degree angle sensors are compared. The robot then turns in the direction where the sensor measures a greater distance, ensuring it moves towards a clearer path. This turning process is accompanied by an increment of a counter, which keeps track of the number of hard 90-degree turns made. This counter is essential for stopping the robot after it completes 12 turns.

Meanwhile, the sensors positioned at 45-degree angles are continuously active, ensuring the vehicle avoids hitting any balls along its path. They provide early warnings about obstacles that might not be directly in front but are on the sides, helping the robot to avoid collisions.

Flow Diagram for Robot Navigation

Here is the step-by-step detailed flow diagram for the robot's navigation process:
Start
Move Straight
Front Sensor Check (Is the front sensor value less than the threshold?)
No: Continue moving straight
Yes: Compare left and right 90-degree sensor values
Compare 90-Degree Sensor Values (Which side has a greater distance?)
Left: Turn Left
Right: Turn Right
Increment Turn Counter
Turn Counter Check (Is the turn counter less than 12?)
Yes: Continue moving straight
No: Stop Robot
45-Degree Sensor Check (Do 45-degree sensors detect a wall?)
No: Continue moving straight
Yes: Avoid Wall and then continue moving straight


Pseudo code

Initialize sensors
Set threshold distance
Set turn counter to 0

while turn counter < 12:
    Move robot straight
    if front sensor value < threshold:
        if left 90-degree sensor value > right 90-degree sensor value:
            Turn robot left
        else:
            Turn robot right
        Increment turn counter
    
    if left 45-degree sensor detects ball:
        Avoid ball
    if right 45-degree sensor detects ball:
        Avoid ball

Stop robot


In Obstacle Round , the robot follows a similar logic as in Round 1, with the addition of a Pixy camera to enhance obstacle detection and navigation. The Pixy camera detects obstacles and determines their color. Depending on the color detected, the robot's servo motor is turned accordingly:

If the obstacle is red, the servo motor turns the robot right.

If the obstacle is green, the servo motor turns the robot left.

Pseudo code

Initialize sensors and Pixy camera
Set threshold distance
Set turn counter to 0

while turn counter < 12:
    Move robot straight
    if front sensor value < threshold:
        if left 90-degree sensor value > right 90-degree sensor value:
            Turn robot left
        else:
            Turn robot right
        Increment turn counter
    
    if Pixy camera detects obstacle:
        if color is red:
            Turn robot right
        if color is green:
            Turn robot left
    
    if left 45-degree sensor detects wall:
        Avoid wall
    if right 45-degree sensor detects wall:
        Avoid wall

Stop robot

