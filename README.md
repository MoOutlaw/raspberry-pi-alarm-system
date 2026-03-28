# Raspberry Pi Motion Alarm System

A Python-based IoT security alarm built on a Raspberry Pi that detects motion using a PIR sensor, triggers visual and audio alerts, and sends an automated email notification to a configured recipient. Developed as part of an IoT module at Coventry College, the project demonstrates practical integration of hardware components and Python software into a working security system.

---

## Module Context

**Module:** Internet of Things (IoT)
**Institution:** Coventry College
**Level:** National Extended Diploma in IT (Level 3)

---

## Tech Stack

**Hardware:**
- Raspberry Pi
- PIR (Passive Infrared) Motion Sensor
- Red and Blue LEDs
- Buzzer

**Language:** Python 3

**Libraries:**
- `gpiozero` — GPIO pin control for sensors and output components
- `smtplib` — SMTP email transmission
- `email` — Email message construction and formatting

---

## How It Works

When the PIR sensor detects movement, the system responds immediately across three channels:

1. **Visual alert** — the red and blue LEDs activate to provide a clear on-device indication of motion
2. **Audio alert** — the buzzer triggers an audible alarm
3. **Email notification** — an automated email is sent to a pre-configured recipient with details of the motion event

The system runs continuously, monitoring for motion in real time and resetting between detections.

---

## Features

- Real-time motion detection using a PIR sensor connected via GPIO
- Dual LED indicators (red and blue) that activate on motion trigger
- Buzzer alarm for audible alerting
- Automated email notification sent via SMTP on each detection event
- Continuous monitoring loop with reset between triggers

---

## Wiring & GPIO Pin Configuration

| Component | GPIO Pin |
|---|---|
| PIR Motion Sensor | GPIO 17 |
| Red LED | GPIO 18 |
| Blue LED | GPIO 24 |
| Buzzer | GPIO 22 |

Ensure all components are connected correctly before running the script. Incorrect wiring may damage the GPIO pins.

---

## How to Run

**Prerequisites:**
- Raspberry Pi with Raspberry Pi OS installed
- Python 3 installed
- Required libraries installed:

```bash
pip install gpiozero
```

`smtplib` and `email` are part of the Python standard library and require no additional installation.

**Step 1 — Connect the hardware**

Wire each component to the GPIO pins listed in the table above.

**Step 2 — Configure email credentials**

Open `alarm_system.py` and update the following fields with your email details:

```python
SENDER_EMAIL = "your_email@gmail.com"
SENDER_PASSWORD = "your_app_password"
RECIPIENT_EMAIL = "recipient@example.com"
```

If using Gmail, you will need to generate an App Password from your Google Account security settings rather than using your main account password.

**Step 3 — Run the system**

```bash
python alarm_system.py
```

The system will begin monitoring immediately. Motion events will trigger alerts and send an email notification automatically.

---

## Repository Structure

```
├── alarm_system.py        # Main application — motion detection and alert logic
├── Alarm System.pdf       # Full project report and documentation
└── README.md
```

---

## Key Skills Demonstrated

- IoT hardware integration — wiring and controlling sensors and output components via GPIO
- Python scripting for real-time event-driven systems
- Networked alerting using SMTP email automation
- Embedded systems thinking — designing software around hardware constraints and pin configuration
- Technical documentation and project reporting
