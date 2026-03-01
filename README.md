# Traffic-Light-Embedded-System
Overview

This project implements a smart traffic light control system using an Arduino microcontroller and an ultrasonic sensor to detect vehicles. Unlike traditional fixed-time traffic signals, the system dynamically adjusts signal timing based on traffic presence.
The aim of the project was to demonstrate embedded system development, sensor integration, and real-time control logic using a microcontroller-based system.

Features
Vehicle detection using ultrasonic sensor (HC-SR04)
Adaptive traffic light timing
Real-time embedded control
LED-based traffic signal simulation (Red, Yellow, Green)
State-machine traffic control logic

Hardware Components
Arduino Uno
Ultrasonic Sensor (HC-SR04)
Red LED
Yellow LED
Green LED
220Ω Resistors
Breadboard
Jumper wires
USB power supply

System Architecture
The system uses sensor feedback to adjust traffic signal timing.
System flow:
Vehicle Detection → Traffic Analysis → Signal Decision → LED Control
If a vehicle is detected close to the sensor, the green signal duration increases.
If no vehicle is detected, the system switches signals faster.
This simulates a basic adaptive traffic control system.

Circuit Configuration
Red LED → Pin 8
Yellow LED → Pin 9
Green LED → Pin 10
Ultrasonic Trigger → Pin 6
Ultrasonic Echo → Pin 7

Example Arduino Code
int red = 8;
int yellow = 9;
int green = 10;
int trigPin = 6;
int echoPin = 7;
long duration;
int distance;
void setup() {
  pinMode(red, OUTPUT);
  pinMode(yellow, OUTPUT);
  pinMode(green, OUTPUT);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  Serial.begin(9600);
}
void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);
  distance = duration * 0.034 / 2;
  if(distance < 20){
    digitalWrite(red, LOW);
    digitalWrite(green, HIGH);
    delay(6000);
    digitalWrite(green, LOW);
    digitalWrite(yellow, HIGH);
    delay(2000);
    digitalWrite(yellow, LOW);
    digitalWrite(red, HIGH);
    delay(4000);
  }
  else{
    digitalWrite(red, LOW);
    digitalWrite(green, HIGH);
    delay(3000);
    digitalWrite(green, LOW);
    digitalWrite(yellow, HIGH);
    delay(2000);
    digitalWrite(yellow, LOW);
    digitalWrite(red, HIGH);
    delay(3000);
  }
}

Testing and Results
The system was tested to verify:
Accurate vehicle detection using the ultrasonic sensor
Stable traffic signal transitions
Reliable microcontroller control
The prototype successfully demonstrates a basic smart traffic signal system using sensor-based input.

Skills Demonstrated
Embedded Systems Development
Arduino Programming
Sensor Integration
Real-Time Control Systems
Hardware Prototyping
Circuit Debugging

Future Improvements
Multiple lane traffic detection
IoT traffic monitoring dashboard
Smart city traffic management integration
AI-based traffic optimisation
