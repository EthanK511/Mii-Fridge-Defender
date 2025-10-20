# Mii Fridge Defender — Build Instructions

**Important:** This project is strictly **non-harmful**. Only audio/visual alerts are used. Inform anyone nearby before enabling sensors or optional logging.

---

## Step 1 — Wiring

### HC-SR04 Ultrasonic Sensor
- VCC -> 5V
- GND -> GND
- TRIG -> D2
- ECHO -> D3

### NeoPixel LED / Strip
- DIN -> D6
- 5V -> 5V
- GND -> GND
- Optional: 470Ω resistor in series with DIN, 1000 µF cap across 5V/GND

### Buzzer
- Passive buzzer: + -> D9, - -> GND
- Active buzzer: use `digitalWrite()` instead of `tone()` in code

### Button (Arm/Disarm)
- One leg -> D4
- Other leg -> GND
- Using INPUT_PULLUP in code

### Power
- Arduino Nano powered via USB (wall adapter or power bank)
- Common ground for all components

---

## Step 2 — Mounting in Hack Pack Turret
1. Mount HC-SR04 facing fridge door handle. Use turret bracket or tape.  
2. Mount NeoPixel where it is visible.  
3. Mount buzzer inside turret box, sound facing outward.  
4. Route wires to avoid pinching or sharp bends.  
5. Lock or secure turret servos if used.

---

## Step 3 — Software Setup
1. Install Arduino IDE (or PlatformIO).  
2. Install `Adafruit_NeoPixel` library.  
3. Open `mii_fridge_defender_nano.ino`. Configure:
   - `DIST_THRESHOLD_CM`  
   - `NUM_PIXELS`  
   - Pin assignments if different  
4. Select board: Tools → Board → Arduino Nano  
5. Upload sketch.  
6. Open Serial Monitor at 115200 for debugging.

---

## Step 4 — Calibration
1. Power system and position turret at final location.  
2. Observe Serial prints while opening fridge.  
3. Adjust `DIST_THRESHOLD_CM` so it triggers reliably.  
4. Tune `TRIGGER_COOLDOWN_MS` to prevent repeated triggers.  
5. Optional: add software filter if false positives occur.

---

## Step 5 — Operation
- Short button press → toggle Armed/Disarmed  
- Long button press (>1s) → mute/unmute buzzer  
- NeoPixel LED indicates armed state:
  - Green = armed  
  - Blue = disarmed  
  - Yellow = muted  

---

## Step 6 — Optional Features
- Wi-Fi notification using ESP32/ESP8266 (Nano cannot send webhooks)  
- Photo logging (only with consent)  
- IFTTT push notifications for fridge open events

---

## Troubleshooting
- **No Serial Output:** check USB/port/board selection.  
- **Sensor always reads -1:** check HC-SR04 wiring, power, or distance out of range.  
- **NeoPixel flicker:** check 5V supply, add 470Ω resistor & 1000 µF capacitor.  
- **Buzzer silent:** passive vs active buzzer wiring mismatch.  
- **False triggers:** adjust distance threshold, add software filter, or use contact sensor.
