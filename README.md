# 5. Touchpad-Controlled Autonomous Vehicle

### Real-Time Wireless Embedded Vehicle Control with Ultrasonic Safety Integration

🔧 **Tech Stack:** STM32F401RE, ESP32 (Dual Modules), Embedded C, ESP-NOW, I2C, SPI, PWM, HC-SR04 Ultrasonic Sensors, IBT-2 Motor Drivers, TSC2046 Touch Controller  

---

## 🧠 Overview

The Touchpad-Controlled Autonomous Vehicle is a dual-mode embedded system that enables low-latency wireless manual control through a resistive touchpad while incorporating ultrasonic-based obstacle detection for safety.  

The architecture separates wireless communication and real-time motor control across ESP32 and STM32 microcontrollers to achieve deterministic performance and modular system design.

---

## 🎯 Objective

- Implement responsive touch-based vehicle control  
- Achieve reliable peer-to-peer wireless communication  
- Integrate multi-sensor obstacle detection  
- Develop structured embedded firmware with real-time behavior  
- Demonstrate modular multi-microcontroller system design  

---

## 🏗️ System Architecture

### 🔹 Controller Module (User Interface Side)

**Components:**
- ESP32 (Transmitter)
- Resistive Touchpad
- TSC2046 Touch Controller (SPI Interface)

**Operation:**
- Touchpad generates analog X/Y coordinate signals  
- TSC2046 digitizes coordinates via SPI  
- ESP32 packages coordinate data into compact frames  
- Data transmitted wirelessly using ESP-NOW  

---

### 🔹 Vehicle Module (Car Side)

**Components:**
- ESP32 (Receiver)
- STM32F401RE (Main Control Unit)
- IBT-2 Motor Drivers
- 4 DC Motors
- 3 HC-SR04 Ultrasonic Sensors  

**Operation:**
- ESP32 receives wireless packets  
- Coordinates forwarded to STM32 via I2C  
- STM32 maps touch regions to directional commands  
- PWM signals generated to control motor speed and direction  
- Ultrasonic sensors continuously monitored for obstacle detection  

---

## 🔄 Operating Modes

### 🚘 Drive Mode (Manual Touch Control)

- Touchpad divided into directional regions:
  - Forward  
  - Backward  
  - Left  
  - Right  
  - Stop  
- STM32 generates timer-based PWM signals  
- Differential motor control enables turning  
- Touch filtering and hysteresis eliminate jitter  

---

### 🛑 Ultrasonic Safety Mode

Activated via onboard push button.

- STM32 reads 3 ultrasonic sensors (Front, Left, Right)  
- If obstacle distance < 30 cm:
  - Immediate motor halt  
- Timeout handling and distance smoothing prevent false triggers  

---

## 🛠️ Key Embedded Features

- ESP-NOW low-latency peer-to-peer wireless communication  
- Structured I2C communication between ESP32 and STM32  
- Timer-based PWM motor control  
- SPI-based touch data acquisition  
- Real-time state-machine firmware logic  
- Sensor data validation and filtering  
- Automatic safety-stop mechanism  

---

## 📡 Communication Flow

Touchpad  
→ SPI  
→ ESP32 Transmitter  
→ ESP-NOW  
→ ESP32 Receiver  
→ I2C  
→ STM32  
→ PWM  
→ Motor Driver  
→ Motors  

Ultrasonic Sensors  
→ STM32  
→ Distance Evaluation  
→ Safety Control  

---

## 🧪 Embedded Techniques Implemented

- Touch signal filtering and hysteresis logic  
- Packet validation for wireless reliability  
- Timeout management for ultrasonic echo  
- Deterministic state-based control architecture  
- Multi-microcontroller task separation  

---

## 🚀 Performance Highlights

- Low-latency real-time response  
- Stable directional transitions without oscillation  
- Reliable multi-sensor obstacle detection  
- Robust wireless communication under continuous testing  

---

## 🔮 Future Enhancements

- Encoder-based closed-loop speed control  
- PID motor stabilization  
- Battery monitoring system  
- OLED diagnostics interface  
- Semi-autonomous navigation expansion  

---

## 👨‍💻 Developed By

Tirth Patel  
Embedded Systems | Firmware Development | Real-Time Control Systems  

---
