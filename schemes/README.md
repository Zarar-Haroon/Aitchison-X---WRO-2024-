Electromechanical diagrams
====

## Power Supply:

Lipo Battery connected to a Buck-Boost Converter.

Buck-Boost Converter outputs 12V to the Motor Driver L298N.

Three Lithium-Ion Cells connected to a Buck Converter.

Buck Converter outputs 5V to the Arduino Mega and other 5V components.

## Arduino Mega:

Connected to various sensors and modules.

Pixy Camera connected to one of the digital I/O pins.

Ultrasonic Sensors connected to multiple digital I/O pins (one at the front, two at 90 degrees, and two at 45 degrees).

DC Motor controlled via the Motor Driver L298N.

Servo Motor connected to a PWM pin.

## Motor Driver L298N:

Inputs connected to the Arduino Mega for control.

Outputs connected to the DC Motor.

## Connections:

Ultrasonic Sensors:
    Front Sensor to D2
    Left 90-degree Sensor to D3
    Right 90-degree Sensor to D4
    Left 45-degree Sensor to D5
    Right 45-degree Sensor to D6

Pixy Camera to D7

DC Motor to Motor Driver Output

Servo Motor to PWM pin D9

Power lines from Buck Converter to Arduino and sensors (5V and GND)

Power lines from Buck-Boost Converter to Motor Driver (12V and GND)


## Circuit diagram:

Lipo Battery -> Buck-Boost Converter -> Motor Driver L298N -> DC Motor

Three Lithium-Ion Cells -> Buck Converter -> 5V Components (Arduino Mega, Sensors, Pixy Camera, Servo Motor)

Arduino Mega: Digital I/O Pins for Sensors and Pixy Camera

Motor Driver L298N Inputs connected to Arduino Mega

Servo Motor connected to PWM Pin on Arduino Mega
