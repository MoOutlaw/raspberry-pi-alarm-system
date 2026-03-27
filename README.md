# 🔔 Raspberry Pi Motion Alarm System

A Python-based IoT security alarm built on a Raspberry Pi that detects motion using a PIR sensor, triggers visual and audio alerts, and sends an email notification.

## 🛠 Tech Stack
- **Hardware:** Raspberry Pi, PIR Motion Sensor, LEDs, Buzzer
- **Language:** Python 3
- **Libraries:** gpiozero, smtplib, email

## ⚙️ Features
- Real-time motion detection via PIR sensor
- Red/Blue LED indicators on motion trigger
- Buzzer alarm activation
- Automated email alert sent to a configured recipient

## 🚀 How to Run
1. Connect PIR sensor to GPIO pin 17, Red LED to pin 18, Blue LED to pin 24, Buzzer to pin 22.
3. Update the email credentials in `alarm_system.py`.
4. Run the script:
```bash
   python alarm_system.py
```

## 📂 Project Structure
## 📄 Documentation
Full project report available in the `Alarm System.pdf` folder.

## 🎓 Context
Developed as part of an IoT module at college, demonstrating integration of hardware and software components.
