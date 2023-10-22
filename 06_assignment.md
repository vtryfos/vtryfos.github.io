---
title: 06_assignment
layout: default
---

# **Input and Output: Measuring and corresponding to data values**  

For this week’s assignment, the main task was to utilize a microcontroller’s applications. This microcontroller can take various measurements such as temperature, humidity, position in space and so on (input) and those can be used to either explain or point out theories and observations (output). In my case, I used two different microcontrollers, with the first one being the Arduino Uno v3 and the second one being the Adafruit feather nrf52840 sense sensor (Figure 1).





Figure 1: Figure 1 shows the microcontrollers and the sensors used to measure relevant data to the main project.
## **First set of measurements**
Both of the aforementioned microcontrollers were programmed to measure data that are relevant to my semester project; the floating buoy. The main microcontroller that I utilize the most for the needs of my project is the Adafruit feather. This microcontroller is equipped with 2 valuable sensors that concern my project; the LSM6DS33 Accel/Gyro and the LIS3MDL magnetometer, as I am interested in measuring the buoy’s direction/orientation and the wave height by calculating it through the recorded displacement of the buoy in the z-axis. Those two measure the microcontroller’s direction by measuring gravity or the three dimensional rate of acceleration  (3-axis accelerometer), its spin and twist in space (3-axis gyroscope), and lastly, the magnetic field that surrounds the microcontroller (3-axis magnetometer). Combining those three sensors, a 9-DoF (degrees of freedom) inertial measurement unit is obtained which can detect the microcontroller’s orientation in space (Industries, n.d.). 

### **Sample rate, method, and data**

In order to get an output (measurements) from the sensor, I used the a code provided in this webpage: [Adafruit Learning System](https://learn.adafruit.com/how-to-fuse-motion-sensor-data-into-ahrs-orientation-euler-quaternions/overview). In addition to that, I also followed the same method as they did, namely, the method that uses the sensors combined output to visualize an object’s real time 3D-orientation. 

There are in general many factors that could eventually affect the quality of my measurements. To avoid that, it is important to have high resolution while measuring, meaning that the sampling rate of the sensors should be high. In this case, the code that I utilized had as a default a 100 Hz sampling rate (100 measurements per second), which is a rather satisfying rate to sample with. Additionally, the code prints only one tenth (1/10) of the obtained measurements. Lastly, the code also contains three different filters (Mahony, Madqwick, NXP Sensor Fusion) that together with the sensors give me the best possible measurements. For the needs of my project, I decided that the Mahony filter is more than capable of doing the job. Further information and documentation of those three filter can be found in the following webpage: Sensor Fusion Algorithms | How to Fuse Motion Sensor Data into AHRS Orientation (Euler/Quaternions) | Adafruit Learning System, as I don’t think that dwelling into such technicalities is relevant to this assignment.
Having the code in place, I had to then calibrate the magnetometer. The magnetometer was calibrated by using an interface suggested by the website cited above, called MotionCal (PJRC Store), and is depicted in Figure 2. 


![Screenshot 2023-10-18 231308](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/09a14928-f3d4-4cab-8e02-29efe7a99d73)
Figure 2: Shows the interface where the LIS3MDL was calibrated.

At this point, I had the needed tools in place in order to get a 3D-orientation in real space. 




https://github.com/vtryfos/vtryfos.github.io/assets/143755086/c300659a-6bdb-472a-9803-6202e5d68590


### **Power consumption**

## **Second set of measurements**
Another aspect of the floating buoy is its ability to recharge the battery on-board. As mentioned during the previous assignments, a rotating pendulum will be mounted inside the buoy’s housing. The role of this pendulum is to initiate an energy transformation, from wave/mechanical to electrical, as described previously. Firstly, it is essential to see whether the pendulum has a sufficient rate of rotations, meaning that it is important to know if the pendulum rotates fast enough per minute to actually initiate the energy conversion described above. To achieve that, I had to find an appropriate sensor and method that measures the pendulum’s RPM.  

### **Sample rate and data**
### **Power consumption**


