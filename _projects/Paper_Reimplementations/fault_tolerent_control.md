---
title: Fault Tolerant Control of UAV
subtitle: Single Motor Failure Recovery
contributors: Arnav Kharbanda*, Sai Susant*, Nalin Angrish*, Abhigyan Singh*, Tanya*, Navnoor Singh* 
date: 2022-01-01
# image: ../images/raceline.png
order: -30
---

Report Link:- [Report](https://drive.google.com/file/d/1yOOwa6ikZ7ycm5P9IPuu0d4UvInRn0Q9/view?usp=sharing)

Code Link:- [Github](https://github.com/Arker123/Fault-Tolerent-Control)

### Position and Altitude Control of Quadrotor with Single Motor Failure

#### Abstract
This project develops a robust control algorithm for quadrotors to maintain stability during motor failures, crucial for UAV safety in surveillance and mapping applications. It includes a fault detection algorithm based on a **quasi-linear Parameter Varying (qLPV)** observer and **Fault Tolerant Control (FTC)** methods. The system ensures stable flight by adjusting the remaining motors and supporting controlled landing, stable hover, and basic navigation.

#### Challenges
1. **Failure Detection**: Quick, real-time identification of motor failure.
2. **Control Adjustments**: Real-time motor adjustments to maintain stability after failure.

#### Solution
Using the **IRIS quadrotor model** in **Gazebo simulator**, a **PX4 flight controller** was developed to:
- Detect motor failure using **qLPV PIO**.
- Transition to **Fault-Tolerant Control (FTC)**, using **control allocation** to adjust motor contributions and maintain stability.

#### Results
- **Fault Detection**: The system detected motor failures in **417 ms** and maintained control in various conditions.
- **Fault-Tolerant Control**: Successfully kept the quadrotor stable during a motor failure and guided it to a safe landing without crashes.

#### Conclusion
This project demonstrates an effective fault detection and fault-tolerant control system for quadrotors, ensuring stability and safe operation despite motor failures. Further testing is planned to enhance the system's robustness under diverse conditions.
