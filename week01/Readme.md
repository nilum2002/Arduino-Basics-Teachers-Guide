# Arduino Basics for School Students

## Lesson Topic: Ultrasonic Sensor (HC-SR04)

---

# 1. Lesson Overview

**Target Group:** School students (Beginner level)
**Lesson Duration:** 1.5 – 2 hours
**Lesson Type:** Practical + Theory

### Learning Objectives

By the end of this lesson, students will be able to:

* Understand what an ultrasonic sensor is
* Explain how distance measurement works using sound waves
* Identify HC-SR04 sensor pins
* Connect an ultrasonic sensor to Arduino correctly
* Upload and run a test program
* Measure distance using Arduino Serial Monitor
* Build a simple obstacle detection system

---

# 2. Introduction to Ultrasonic Sensors

An **Ultrasonic Sensor** is a device used to measure distance using **sound waves**.

It works by:

1. Sending ultrasonic sound waves
2. Receiving the reflected waves
3. Calculating how long they take to return
4. Converting time into distance

Example uses:

* Robot obstacle detection
* Automatic doors
* Parking sensors in cars
* Water level measurement
* Distance measuring devices

---

# 3. What is Sound Reflection?

Ultrasonic sensors work based on **echo**.

Example:

If you shout near a wall:

Sound travels → hits wall → returns back

This returning sound is called an **echo**

Ultrasonic sensors use this same idea.

---

# 4. HC-SR04 Ultrasonic Sensor

The most common ultrasonic sensor used with Arduino is:

**HC-SR04**

It has 4 pins:

| Pin  | Function        |
| ---- | --------------- |
| VCC  | Power (5V)      |
| GND  | Ground          |
| TRIG | Sends signal    |
| ECHO | Receives signal |

---

# 5. Working Principle of HC-SR04

Step-by-step operation:

Step 1
Arduino sends signal to TRIG pin

Step 2
Sensor sends ultrasonic wave

Step 3
Wave hits object and returns

Step 4
ECHO pin becomes HIGH

Step 5
Arduino measures time taken

Step 6
Distance is calculated

Formula used:

Distance = (Speed × Time) / 2

Speed of sound:

343 m/s

Division by 2 happens because sound travels forward and backward.

---

# 6. Required Components

Students need:

* Arduino Uno
* HC-SR04 Ultrasonic Sensor
* Breadboard
* Jumper wires
* USB cable
* Computer with Arduino IDE

---

# 7. Circuit Connection

Make the following connections:

| Sensor Pin | Arduino Connection |
| ---------- | ------------------ |
| VCC        | 5V                 |
| GND        | GND                |
| TRIG       | Pin 9              |
| ECHO       | Pin 10             |

---

# 8. First Test Program (Distance Measurement)

Upload this program to Arduino.

### Arduino Code

```cpp
#define trigPin 9
#define echoPin 10

long duration;
int distance;

void setup()
{
  Serial.begin(9600);

  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
}

void loop()
{
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);

  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);

  distance = duration * 0.034 / 2;

  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  delay(500);
}
```

---

# 9. Code Explanation (Line by Line)

### Step 1

Define pins

```cpp
#define trigPin 9
#define echoPin 10
```

These lines assign Arduino pins.

---

### Step 2

Create variables

```cpp
long duration;
int distance;
```

duration stores time
distance stores calculated distance

---

### Step 3

Start Serial Monitor

```cpp
Serial.begin(9600);
```

Used to display distance on computer

---

### Step 4

Set pin modes

```cpp
pinMode(trigPin, OUTPUT);
pinMode(echoPin, INPUT);
```

TRIG sends signal
ECHO receives signal

---

### Step 5

Send ultrasonic signal

```cpp
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

digitalWrite(trigPin, HIGH);
delayMicroseconds(10);

digitalWrite(trigPin, LOW);
```

This generates ultrasonic pulse

---

### Step 6

Read return signal

```cpp
duration = pulseIn(echoPin, HIGH);
```

Measures time taken for echo return

---

### Step 7

Convert time to distance

```cpp
distance = duration * 0.034 / 2;
```

Formula converts time into centimeters

---

### Step 8

Print result

```cpp
Serial.print("Distance: ");
Serial.print(distance);
Serial.println(" cm");
```

Displays distance on screen

---

# 10. How to Test the Sensor

Follow these steps:

Step 1
Upload code

Step 2
Open Serial Monitor

Step 3
Select baud rate 9600

Step 4
Place hand in front of sensor

Step 5
Observe distance change

Students will see real-time measurements.

---

# 11. Activity for Students

### Activity 1

Measure distance of:

* Book
* Pencil box
* Wall
* Hand

Write results in table:

| Object | Distance |
| ------ | -------- |
| Book   |          |
| Wall   |          |
| Hand   |          |

---

# 12. Mini Project (Obstacle Detection Alert)

Add LED when object is near.

Extra components:

* LED
* 220Ω resistor

---

# Connection Table

| Component | Arduino Pin |
| --------- | ----------- |
| LED +     | Pin 7       |
| LED –     | GND         |

---

# Program with LED Alert

```cpp
#define trigPin 9
#define echoPin 10
#define ledPin 7

long duration;
int distance;

void setup()
{
  Serial.begin(9600);

  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(ledPin, OUTPUT);
}

void loop()
{
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);

  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);

  distance = duration * 0.034 / 2;

  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  if(distance < 10)
  {
    digitalWrite(ledPin, HIGH);
  }
  else
  {
    digitalWrite(ledPin, LOW);
  }

  delay(500);
}
```

---

# 13. Expected Output

If object distance is:

Less than 10 cm → LED ON
Greater than 10 cm → LED OFF

Students build their first obstacle detector.

---

# 14. Common Errors Students Make

Wrong wiring
TRIG and ECHO swapped
Wrong baud rate
Loose jumper wires
Sensor facing wrong direction

Always check connections carefully.

---

# 15. Teacher Demonstration Idea

Show:

Hand moving closer → distance decreases
Hand moving away → distance increases

Then ask students:

Why does distance change?

This improves conceptual understanding.

---

# 16. Homework Task

Modify program so LED turns ON when object is closer than:

20 cm instead of 10 cm

Students only change one value:

```cpp
if(distance < 20)
```

---