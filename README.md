# UltraGPS — Indoor Ultrasonic Localization System

An Arduino-based indoor localization system for a **RTK mini-tractor**, capable of real-time tracking in **GPS-denied environments**.  
Built with ultrasonic sensors, RF synchronization, and MATLAB trilateration algorithms to achieve **±2 cm accuracy at 5 Hz**.

---

## 🛰️ Project Overview
**UltraGPS** was designed to provide precise, low-cost indoor positioning for small autonomous vehicles used in educational robotics programs.  
The system uses a **transmitter mounted on a mini-tractor** and **six fixed receiver nodes** arranged around the environment to calculate position via **ultrasonic Time-of-Flight (ToF)**.

---

## ⚙️ Core Contributions

- **Developed** an indoor localization system for an RTK mini-tractor using Arduino and ultrasonic sensors, enabling real-time tracking in GPS-denied environments across four high-school robotics programs.  
- **Programmed** synchronization and Time-of-Flight routines in C++, ensuring consistent, low-latency data across six receiver nodes.  
- **Implemented** real-time position tracking in MATLAB, achieving ±2 cm accuracy and stable 5 Hz update rates.  
- **Designed** the transmitter tower, receiver mounts, and enclosures in SolidWorks, optimizing rapid setup and portability.  
- **Reduced** calibration time by 80% (10 → 2 minutes) through algorithmic and UI improvements in the calibration software.

---

## 🧩 System Architecture

**Transmitter (on robot)**
- Arduino-based pulse generator for six ultrasonic transmitters  
- RF trigger synchronization (NRF24L01 modules)  
- Powered by onboard battery  

**Receivers (fixed nodes)**
- Six Arduino receivers capturing echo timing  
- Converts ToF signals to distance measurements  
- Sends data to host via serial or Ethernet  

**Host Computer (MATLAB)**
- Performs ToF → distance conversion  
- Executes multilateration and real-time plotting  
- Displays live position of the tractor  

---

## 🛠️ Technologies Used

| Category | Tools & Frameworks |
|-----------|-------------------|
| **Hardware** | Arduino Uno/Nano, HC-SR04 ultrasonic sensors, NRF24L01 RF modules |
| **Software** | C++ (Arduino IDE), MATLAB |
| **Design** | SolidWorks (tower, mounts, enclosures) |
| **Version Control** | Git & GitHub |

---

## 🚀 Getting Started

### 1️⃣ Hardware Setup
1. Position six ultrasonic receivers around the area (≈ 1 m apart).  
2. Mount the transmitter tower on the robot.  
3. Connect NRF24L01 modules for wireless synchronization between TX and RX Arduinos.

### 2️⃣ Arduino Configuration
- Open `transmitter/tx.ino` and `receivers/rx.ino` in Arduino IDE.  
- Install required libraries:  
  - `RF24` by TMRh20  
  - `NewPing` (for HC-SR04)  
- Upload code to both transmitter and receiver boards.

### 3️⃣ MATLAB Visualization
- Open `host/ultragps_localize.m`.  
- Configure:
  ```matlab
  SERIAL_PORT = "COM3";       % adjust to your system
  anchors = [x1, y1; x2, y2; ... x6, y6];
