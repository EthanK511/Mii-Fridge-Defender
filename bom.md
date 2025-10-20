# Mii Fridge Defender — Bill of Materials (BOM)

This document lists all components needed to build the Mii Fridge Defender using an Arduino Nano and a Hack Pack IR Turret build box. This project is for **non-harmful audio/visual alerts only**.

## Electronics

| Qty | Component | Notes |
| --- | --------- | ----- |
| 1 | Arduino Nano (ATmega328P) | Main controller |
| 1 | HC-SR04 Ultrasonic Distance Sensor | Trig, Echo, Vcc, GND |
| 1 | Adafruit NeoPixel WS2812 LED or small strip | Visual status & trigger animation |
| 1 | Passive piezo buzzer | Use active buzzer differently; see instructions |
| 1 | Momentary push button | Arm/disarm toggle; connects to GND and digital pin |
| 1 | USB cable | Power Arduino Nano |
| 1 | 5V power supply | USB wall adapter or battery pack |
| N/A | Jumper wires / breadboard / prototype PCB | For wiring |
| N/A | Heat shrink tubing / tape / zip ties | Optional for cable management |

## Mechanical / Mounting

| Qty | Component | Notes |
| --- | --------- | ----- |
| 1 | CrunchLabs Hack Pack IR Turret build box | Chassis, mounts, brackets |
| N/A | Screws / double-sided tape | Mount sensor, NeoPixel, buzzer |
| N/A | Servo / turret mounts (optional) | If available, for sensor positioning |

## Optional

| Qty | Component | Notes |
| --- | --------- | ----- |
| 1 | Small status LED | Optional, shows armed/disarmed |
| 1 | Camera module | Optional; only if all users consent |
