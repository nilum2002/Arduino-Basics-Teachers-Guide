# Arduino Basics – Servo Motors

## Introduction to Servo Motors

A servo motor is a special type of motor that can rotate to a specific angle with high accuracy. Unlike normal DC motors that rotate continuously, servo motors move to a controlled position.

Servo motors are widely used in:

* Robots
* Automatic doors
* RC cars and airplanes
* Camera systems
* Industrial machines

In Arduino projects, servo motors are very popular because they are easy to control using simple code.

---

# Learning Objectives

By the end of this lesson, students will be able to:

* Understand what a servo motor is
* Identify the parts of a servo motor
* Connect a servo motor to Arduino
* Control servo motor angles using Arduino code
* Create simple servo motor projects

---

# Components Required

| Component                   | Quantity |
| --------------------------- | -------- |
| Arduino Uno                 | 1        |
| Servo Motor (SG90 or MG90S) | 1        |
| Breadboard (optional)       | 1        |
| Jumper Wires                | Several  |
| USB Cable                   | 1        |
| Computer with Arduino IDE   | 1        |

---

# What is a Servo Motor?

A servo motor is a motor with:

* A DC motor inside
* A gear system
* A position sensor
* A control circuit

The servo receives signals from the Arduino and moves to the requested angle.

Most hobby servo motors can rotate:

* From 0° to 180°

---

# Types of Servo Motors

## 1. Positional Servo Motor

* Moves to a specific angle
* Commonly used with Arduino
* Example: SG90

## 2. Continuous Rotation Servo

* Rotates continuously like a DC motor
* Speed and direction are controlled instead of angle

---

# Servo Motor Wires

Most servo motors have 3 wires.

| Wire Color       | Function |
| ---------------- | -------- |
| Brown or Black   | GND      |
| Red              | VCC (5V) |
| Orange or Yellow | Signal   |

---

# How Servo Motors Work

The Arduino sends PWM (Pulse Width Modulation) signals to the servo motor.

The pulse width tells the servo:

* Which angle to move to
* How long to hold the position

Examples:

* 0° → left side
* 90° → center
* 180° → right side

---

# Connecting the Servo Motor

## Wiring Connections

| Servo Motor | Arduino Uno   |
| ----------- | ------------- |
| GND         | GND           |
| VCC         | 5V            |
| Signal      | Digital Pin 9 |

---

# Circuit Diagram Explanation

* The Arduino provides power to the servo motor
* The signal pin controls the movement angle
* Pin 9 is commonly used for servo control

---

# Arduino Servo Library

Arduino provides a built-in library called:

```cpp
#include <Servo.h>
```

This library makes servo motor control simple.

---

# Basic Servo Motor Program

## Example 1 – Move Servo to 90 Degrees

```cpp
#include <Servo.h>

Servo myServo;

void setup() {
  myServo.attach(9);
}

void loop() {
  myServo.write(90);
}
```

---

# Code Explanation

## Create Servo Object

```cpp
Servo myServo;
```

Creates a servo object named `myServo`.

---

## Attach Servo

```cpp
myServo.attach(9);
```

Connects the servo signal wire to pin 9.

---

## Move Servo

```cpp
myServo.write(90);
```

Moves the servo to 90 degrees.

---

# Example 2 – Sweep Servo Motor

This program rotates the servo from 0° to 180° and back.

```cpp
#include <Servo.h>

Servo myServo;

void setup() {
  myServo.attach(9);
}

void loop() {

  for(int angle = 0; angle <= 180; angle++) {
    myServo.write(angle);
    delay(15);
  }

  for(int angle = 180; angle >= 0; angle--) {
    myServo.write(angle);
    delay(15);
  }

}
```

---

# Program Explanation

## First Loop

```cpp
for(int angle = 0; angle <= 180; angle++)
```

Moves servo from:

* 0°
* to 180°

---

## Second Loop

```cpp
for(int angle = 180; angle >= 0; angle--)
```

Moves servo back:

* 180°
* to 0°

---

# Important Notes

## Power Consumption

Servo motors can draw high current.

For small servos:

* Arduino 5V may work

For larger servos:

* Use an external power supply

---

## Common Problems

| Problem            | Solution           |
| ------------------ | ------------------ |
| Servo shaking      | Check wiring       |
| Servo not moving   | Check power supply |
| Random movement    | Check signal wire  |
| Arduino restarting | Use external power |

---

# Practical Activities

## Activity 1 – Servo Angle Testing

Move servo to:

* 0°
* 45°
* 90°
* 135°
* 180°

Observe the movement.

---

## Activity 2 – Servo Door Simulation

Create a small cardboard door and use the servo to:

* Open the door
* Close the door

---

## Activity 3 – Robot Arm

Use the servo motor as a robotic arm joint.

---

# Real-World Applications

Servo motors are used in:

* Robotic arms
* Drones
* Camera stabilizers
* Industrial automation
* CNC machines
* Automatic gates

---

# Safety Tips

* Do not force the servo by hand
* Use correct voltage
* Disconnect power before rewiring
* Avoid short circuits

---

# Mini Challenge

## Challenge 1

Write a program to:

* Move servo to 0°
* Wait 1 second
* Move to 180°
* Repeat continuously

---

## Challenge 2

Control the servo using a potentiometer.

---

# Advanced Example – Servo Controlled by Potentiometer

## Components Needed

| Component     | Quantity |
| ------------- | -------- |
| Arduino Uno   | 1        |
| Servo Motor   | 1        |
| Potentiometer | 1        |

---

# Wiring Connections

## Potentiometer

| Pin    | Arduino |
| ------ | ------- |
| Left   | GND     |
| Middle | A0      |
| Right  | 5V      |

## Servo

| Servo Wire | Arduino |
| ---------- | ------- |
| GND        | GND     |
| VCC        | 5V      |
| Signal     | Pin 9   |

---

# Potentiometer Servo Code

```cpp
#include <Servo.h>

Servo myServo;

int potPin = A0;
int potValue;
int angle;

void setup() {
  myServo.attach(9);
}

void loop() {

  potValue = analogRead(potPin);

  angle = map(potValue, 0, 1023, 0, 180);

  myServo.write(angle);

  delay(15);
}
```

---

# Code Explanation

## Read Potentiometer

```cpp
analogRead(potPin);
```

Reads analog values from:

* 0 to 1023

---

## Convert to Angle

```cpp
map(potValue, 0, 1023, 0, 180);
```

Converts the potentiometer value into:

* Servo angle

---

# Summary

In this lesson students learned:

* What a servo motor is
* How servo motors work
* How to connect servo motors to Arduino
* How to control angles
* How to create servo motor projects

Servo motors are one of the most important components in robotics and automation projects.

---

# Homework

1. Draw the servo motor wiring diagram.
2. Write a program to move the servo to:

   * 30°
   * 60°
   * 120°
3. Research 5 real-world applications of servo motors.
4. Create a mini project using a servo motor.

---

# Teacher Notes

Recommended lesson duration:

* Theory: 30 minutes
* Practical: 45 minutes
* Activities and discussion: 15 minutes

Recommended servo motor:

* SG90 Micro Servo

Teaching Tips:

* Demonstrate real servo movement
* Let students test different angles
* Encourage hands-on activities
* Explain PWM using simple examples
