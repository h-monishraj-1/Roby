# 🤖 Roby: Gesture-Controlled Robotic Vehicle with Obstacle Detection and Collision Avoidance

Roby is a gesture-controlled robotic vehicle that leverages inertial motion sensing and real-time obstacle detection to provide an intuitive yet fail-safe remote driving experience. Built with ESP-NOW mesh communication, ultrasonic sensing, and differential steering logic, this system demonstrates the practical integration of sensor fusion, embedded systems, and wireless control in robotics.

## 🚀 Features

- 🎮 **Gesture-Controlled Navigation** using MPU6050
- 📡 **ESP-NOW Communication Protocol** for fast, low-power data transmission
- 🧠 **Threshold-Based Pitch/Roll Analysis** for gesture mapping (Forward, Backward, Left, Right, Stop)
- 📏 **Ultrasonic Obstacle Detection** with 35 cm safety threshold
- 🛑 **Fail-Safe Collision Avoidance** with emergency braking and alerts (LED + Buzzer)
- ⚙️ **Differential Steering Control** via dual L298N motor drivers
- 🔄 **Priority Command Resolution** between user input and obstacle detection
- ⚡ **Energy Efficient Design** with modular power distribution
- ⏱️ **Responsive Control** with 1.5s command timeout mechanism

## 🧠 System Architecture

Roby is divided into three ESP8266 units, each with specific responsibilities:

### 1. Gesture Transmitter Unit
- **Components**: ESP8266 + MPU6050
- **Function**: Translates hand orientation into movement commands using:
  - Pitch (Forward/Backward)
  - Roll (Left/Right)
- **Communication**: Sends data every 300ms using ESP-NOW
- **Commands**: FORWARD, BACKWARD, LEFT, RIGHT, STOP

### 2. Obstacle Detection Unit
- **Components**: ESP8266 + Ultrasonic Sensor + LED + Buzzer
- **Function**: Continuously checks for obstacles within a 35 cm range
- **Action on Detection**:
  - Local alert via buzzer/LED
  - Sends STOP command to receiver unit via ESP-NOW

### 3. Receiver Unit
- **Components**: ESP8266 + 2x L298N Motor Drivers
- **Function**: Executes motion commands with priority to obstacle signals
- **Logic**:
  - Obstacle STOP has highest priority
  - Gesture inputs only honored when safe
  - Differential steering for smooth turns


## 🛠️ Technologies & Components Used

| Component        | Description |
|------------------|-------------|
| ESP8266          | Wi-Fi microcontroller used in all three units |
| MPU6050          | Inertial sensor for motion (pitch/roll) sensing |
| HC-SR04          | Ultrasonic sensor for obstacle detection |
| L298N            | Dual H-Bridge motor driver |
| DC Motors        | For robotic movement |
| Buzzer & LED     | Alert mechanism for collision warning |
| Power Supply     | Battery packs or USB power |

## 🧪 How It Works

1. The transmitter reads hand motion and sends directional commands wirelessly.
2. The obstacle detection unit monitors distance and overrides movement if danger is detected.
3. The receiver interprets both signals and moves the robot accordingly, prioritizing safety.
4. Movement stops immediately upon obstacle detection even if gesture input continues.

## 💡 Applications

- **Industrial Material Handling Robots**
- **Assistive Mobility Devices**
- **Autonomous Surveillance Systems**
- **Educational Robotics Projects**

## 📈 Performance Highlights

- Stable communication with 300ms command interval
- 1.5s timeout mechanism to prevent hanging commands
- Low-power ESP-NOW protocol enhances battery life
- Obstacle avoidance works seamlessly in real time

## 🔑 Keywords

Gesture-Controlled Robotics, Obstacle Detection, ESP-NOW, MPU6050, Ultrasonic Sensor, Fail-Safe System, Differential Steering, Embedded Control, Sensor Fusion, Emergency Braking, Wireless Communication, Priority Control, Pitch-Roll Analysis

## 🏞️ Images
![WhatsApp Image 2025-05-04 at 03 07 06_ec45fec2](https://github.com/user-attachments/assets/a414e296-510e-4d73-b9bf-9d57bcfce683)
![IMG20250424111219](https://github.com/user-attachments/assets/58d8c667-effd-4bc5-941c-7ec41b4c5530)
![IMG20250424111235](https://github.com/user-attachments/assets/bf2a58ae-6359-4ed2-8875-9e64b8cb7245)



## 📎 License

This project is open-source and available under the MIT License.
