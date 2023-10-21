---
title: 06_assignment
layout: default
---

# **Input and Output: Measuring and corresponding to data values**

For this week’s assignment, the main task was to utilize a microcontroller’s applications. This microcontroller can take various measurements such as temperature, humidity, position in space and so on (input) and those can be used to either explain or point out theories and observations (output). In my case, I used two different microcontrollers, with the first one being the Arduino Uno v3 and the second one being the Adafruit feather nrf52840 sense sensor (Figure 1).


Figure 1: Figure 1 shows the microcontrollers and the sensors used to measure relevant data to the main project.
## **First set of measurements**
Both of the aforementioned microcontrollers were programmed to measure data that are relevant to my semester project; the floating buoy. The main microcontroller that I utilize the most for the needs of my project is the Adafruit feather. This microcontroller is equipped with 2 valuable sensors that concern my project; the LSM6DS33 Accel/Gyro and the LIS3MDL magnetometer, as I am interested in measuring the buoy’s direction/orientation and the wave height by calculating it through the recorded displacement of the buoy in the z-axis. Those two measure the microcontroller’s direction by measuring gravity or the three dimensional rate of acceleration  (3-axis accelerometer), its spin and twist in space (3-axis gyroscope), and lastly, the magnetic field that surrounds the microcontroller (3-axis magnetometer). Combining those three sensors, a 9-DoF (degrees of freedom) inertial measurement unit is obtained which can detect the microcontroller’s orientation in space (Industries, n.d.). 

## **Second set of measurements**
Another aspect of the floating buoy is its ability to recharge the battery on-board. As mentioned during the previous assignments, a rotating pendulum will be mounted inside the buoy’s housing. The role of this pendulum is to initiate an energy transformation, from wave/mechanical to electrical, as described previously. Firstly, it is essential to see whether the pendulum has a sufficient rate of rotations, meaning that it is important to know if the pendulum rotates fast enough per minute to actually initiate the energy conversion described above. To achieve that, I had to find an appropriate sensor and method that measures the pendulum’s RPM.  


