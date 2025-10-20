Mii Fridge Defender — Alarm Edition

A friendly, non‑harmful fridge guardian that detects when your fridge is opened and responds with playful alerts: voice lines, LED patterns, and optional push notifications or photo logging. Designed for roommates, offices, and prank lovers who want awareness without causing harm.

Features

Detects fridge door openings using a distance or contact sensor.

Plays a configurable voice clip or sound effect when triggered.

Runs LED animations (RGB) for visual feedback.

Optional push notifications (IFTTT / Webhook) with timestamp.

Optional photo logging (local camera) — opt‑in only.

Arm/disarm modes, schedule (quiet hours), and manual mute.

Small footprint; fits on or behind a fridge door handle.

Hardware (suggested, replace as desired)

Microcontroller (Arduino Uno R4 WiFi / ESP32 / similar with Wi‑Fi)

Distance or door sensor (e.g., infrared time‑of‑flight sensor, magnetic reed switch, or simple mechanical contact)

Small speaker or audio module (DFPlayer Mini or use microcontroller audio output)

RGB LED (WS2812 / NeoPixel) or an array of LEDs

Optional camera module (USB camera or camera board) — keep privacy in mind

Enclosure, wiring, power supply (USB battery pack or mains adapter)

Use only consumer‑grade, non‑hazardous parts. Do not attach any device intended to harm or startle someone dangerously.

Software overview

Microcontroller firmware: Watch sensor, run LED/sound actions, send webhook on trigger.

Optional server/webhook: Receive events, store logs, forward push notifications (IFTTT, Pushover, Pushbullet, or your own endpoint).

Web UI (optional): View recent events, toggle armed/disarmed, configure messages and schedules.

Quick start — example flow

Install sensor on fridge so it detects door open state.

Load the microcontroller firmware so it:

Monitors the sensor (debounced).

When triggered and armed, plays a short audio clip, shows LED animation, and sends a webhook with a timestamp.

Configure your webhook endpoint or IFTTT to forward push notifications to your phone.

Optionally enable photo capture on trigger (make sure every user is aware and consents).

Example Arduino‑style pseudocode

Below is a minimal, non‑actionable example showing the structure of the firmware (logic only). Adapt for your board / libraries.

// Pseudocode — adapt to your hardware & libraries
const int sensorPin = 2;
const int ledPin = 6;     // e.g., NeoPixel strip or RGB LED
const int buzzerPin = 9;
bool armed = true;
unsigned long lastTrigger = 0;
const unsigned long triggerCooldown = 5000; // 5s debounce/cooldown

void setup() {
  pinMode(sensorPin, INPUT);
  initLEDs();
  initAudio();
  initWiFi();         // optional, for webhook
}

void loop() {
  bool opened = readDoorSensor();
  if (armed && opened && millis() - lastTrigger > triggerCooldown) {
    lastTrigger = millis();
    playVoiceClip("Hey! Hands off my snacks!");
    runLEDAnimation();
    sendWebhookEvent("fridge_opened", nowTimestamp());
  }
  // handle ARMED/DISARM commands (button, web UI, schedule)
}


Notes

readDoorSensor() can be a magnetic reed switch (digital) or a distance sensor threshold.

sendWebhookEvent() should use secure endpoints (HTTPS) and minimal personal data.

Keep voice clips short and non‑startling.

Configuration & customization

Voice / sound: Replace clips with friendly phrases or chimes. Keep volumes reasonable.

LED patterns: Build playful patterns for “armed”, “triggered”, and “silent” states.

Schedules: Add quiet hours so it won’t trigger at night.

Notification settings: Choose push notifications only (no photos) if you prefer privacy.

Access control: Allow a simple PIN or app toggle to disarm temporarily.

Privacy & safety

Inform housemates, coworkers, or family before enabling notification/photo logging.

If using a camera, obtain explicit consent — do not record private spaces or store footage without permission.

Do not design or mount devices that could cause physical harm, startle someone dangerously, or violate local laws. This project is strictly for harmless alerts and theatrics.

Troubleshooting

False triggers: add debounce logic, increase distance threshold, or switch to a contact sensor.

Missing notifications: verify Wi‑Fi credentials, webhook endpoint, and that your microcontroller has internet access.

Audio not playing: check speaker wiring, volume settings, and file format compatibility.

Example project roadmap

v0.1 — Basic sensor + buzzer + LED. Webhook event.

v0.5 — Configurable sound clips, schedules, and web UI.

v1.0 — Optional photo logging (consent flow), multi‑user settings, mobile friendly dashboard.

Contribution

Pull requests welcome. Keep changes aligned with the project’s safety-first, non‑harmful intent. Please include tests or screenshots for UI changes.

License

MIT License — see LICENSE file.
