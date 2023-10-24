---
title: 06_assignment
layout: default
---

# **Input and Output: Measuring and corresponding to data values**  

For this week’s assignment, the main task was to utilize a microcontroller’s applications. This microcontroller can take various measurements such as temperature, humidity, position in space and so on (input) and those can be used to either explain or point out theories and observations (output). In my case, I used two different microcontrollers, with the first one being the Arduino Uno v3 and the second one being the Adafruit feather nrf52840 sense sensor (Figure 1). 

![Merged_document(5)](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/8005c517-6c8f-4692-a74a-b99d2c0384d6)

Figure 1: Figure 1 shows the microcontrollers and the sensors used to measure relevant data to the main project.


## **First set of measurements**
Both of the aforementioned microcontrollers were programmed to measure data that are relevant to my semester project; the floating buoy. The main microcontroller that I utilize the most for the needs of my project is the Adafruit feather. This microcontroller is equipped with 2 valuable sensors that concern my project; the LSM6DS33 Accel/Gyro and the LIS3MDL magnetometer, as I am interested in measuring the buoy’s direction/orientation and the wave height by calculating it through the recorded displacement of the buoy in the z-axis. Those two measure the microcontroller’s direction by measuring gravity or the three dimensional rate of acceleration  (3-axis accelerometer), its spin and twist in space (3-axis gyroscope), and lastly, the magnetic field that surrounds the microcontroller (3-axis magnetometer). Combining those three sensors, a 9-DoF (degrees of freedom) inertial measurement unit is obtained which can detect the microcontroller’s orientation in space (Industries, n.d.). 

### **Sample rate, method, and data**

In order to get an output (measurements) from the sensor, I used the a code provided in this webpage: [Adafruit Learning System](https://learn.adafruit.com/how-to-fuse-motion-sensor-data-into-ahrs-orientation-euler-quaternions/overview). In addition to that, I also followed the same method as they did, namely, the method that uses the sensors combined output to visualize an object’s real time 3D-orientation. 

There are in general many factors that could eventually affect the quality of my measurements. To avoid that, it is important to have high resolution while measuring, meaning that the sampling rate of the sensors should be high. In this case, the code that I utilized had as a default a 100 Hz sampling rate (100 measurements per second), which is a rather satisfying rate to sample with. Additionally, the code prints only one tenth (1/10) of the obtained measurements. Lastly, the code also contains three different filters (Mahony, Madqwick, NXP Sensor Fusion) that together with the sensors give me the best possible measurements. For the needs of my project, I decided that the Mahony filter is more than capable of doing the job. Further information and documentation of those three filter can be found in the following webpage: [Sensor Fusion Algorithms](https://learn.adafruit.com/how-to-fuse-motion-sensor-data-into-ahrs-orientation-euler-quaternions/sensor-fusion-algorithms), as I don’t think that dwelling into such technicalities is relevant to this assignment.
Having the code in place, I had to then calibrate the magnetometer. The magnetometer was calibrated by using an interface suggested by the website cited above, called MotionCal [PJRC Store](https://www.pjrc.com/store/prop_shield.html), and is depicted in Figure 2. 


![Screenshot 2023-10-18 231308](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/09a14928-f3d4-4cab-8e02-29efe7a99d73)
Figure 2: Shows the interface where the LIS3MDL was calibrated.

At this point, I had the needed tools in place in order to get a 3D-orientation in real space but firstly,  it is important to go through and explain the measurements those 3 sensors provide and their units. As mentioned above, I utilize 3 of the sensors that are mounted on the Adafruit board; a gyroscope, an accelerometer, and a magnetometer. 

The sensors return the following values. [Accel, Gyro, and Magnetometer](https://www.adafruit.com/category/521):

* 3-Axis Gyroscope: Measure rotational motion in degrees (dps)
* 3-Axis Accelerometer: Measure acceleration in X, Y, and X-axis (m/s2).
* 3-Axis Magnetometer: Measure and detect magnetic fields and magnetic north respectively (uTelsa).

Now, combining the output of those sensors three different values in total are produced; the pitch, yaw, and roll, or in other words, the Euler angles. The Euler angles describe an object’s 3D orientation around a reference point. [Euler Angles](https://learn.adafruit.com/how-to-fuse-motion-sensor-data-into-ahrs-orientation-euler-quaternions/lets-fuse). More specifically, the pitch, yaw, and roll values are representing an object’s rotation around the Y, Z, and X axis respectively (Figure 3). Those values range between -180° to 180°, depending on the way the object is tilted. The Euler angles can be visually presented in a 3D Model Viewer and will be very useful to calculate wave properties and the buoy’s reaction and response to crashing waves. The visual representation of the Euler angles can be observed in the link below!

[Graphical representation of the sensor's 3D-orientation](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/c300659a-6bdb-472a-9803-6202e5d68590)


![Screenshot 2023-10-23 195420](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/3cf68d01-1ba6-4ec8-a950-e2917c47f4b9)
Figure 3: Representation of the Euler angles (Pitch, Roll, and Yaw) in three dimensions from: [Euler Angles](https://learn.adafruit.com/how-to-fuse-motion-sensor-data-into-ahrs-orientation-euler-quaternions/lets-fuse).



### **Power consumption**
Even though there is a lot of information online, I didn’t manage to find sufficient information about the power consumption of the Adafruit sensor. A good way to measure consumption would be by using a multimeter, however, my limited knowledge about this method prevented me from doing so. The only information I managed to retrieve online was from a Reddit post [How much power does a Feather nRF52840 Express use when using BLE?](https://www.reddit.com/r/adafruit/comments/ypvkgk/how_much_power_does_a_feather_nrf52840_express/) where a user states that the Adafruit sensor draws somewhat less than 10mA. When it comes to powering the sensor up, there are in total two ways for doing so. The first way is via a 5V USB cable that connects to a power source (for example a laptop). The sensor will regulate the USB voltage from 5v down to 3.3V. The second way to power up the sensor is via either a Lithium Polymer or a Lithium Ion battery. The voltage of the battery should range from 3.7 to 4.3 volts [Power Management](https://learn.adafruit.com/adafruit-feather-sense/power-management).


## **Second set of measurements**
Another aspect of the floating buoy is its ability to recharge the battery on-board. As mentioned during the previous assignments, a rotating pendulum will be mounted inside the buoy’s housing. The role of this pendulum is to initiate an energy transformation, from wave/mechanical to electrical, as described previously. Firstly, it is essential to see whether the pendulum has a sufficient rate of rotations, meaning that it is important to know if the pendulum rotates fast enough per minute to actually initiate the energy conversion described above. To achieve that, I had to find an appropriate sensor and method that measures the pendulum’s RPM. Now, given the fact that there are a lot of sensors that can take such samples, I decided to approach a solution from 2 different paths, in other words, by using two different sensors and methods as depicted in Figure 4.

![Merged_document(4)](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/6675ec6b-4fd5-4607-9b99-30e51718c778)
Figure 4: The KY-040 Rotary Encoder and KY-024 Hall Sensor.

### **Sample rate and data**

KY-024 Hall sensor:

The KY-024 Hall sensor is a component that detects a magnetic field. It also provides information about the magnetic field’s polarity and intensity. This sensor returns values closing to 512 when no magnet is present, which is about 2,5 volts according to: [Linear Hall Sensor Guide 49E](https://www.electroschematics.com/linear-hall-sensor/). When passing a magnet in front of the probe, this number will either decrease or increase, depending on the magnet’s polarity. Thus, this magnet can be used to measure RPM of the pendulum if I attach a small and strong magnet to it. Every time this attached magnet passes in front of the sensor’s probe, the sensor will document this event. After some calculations, I was able to retrieve the RPM of a magnet attached to a rotating device I used to test the sensor. This sensor operates by a 5V DC power source.


![Merged_document3)](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/55a08b94-0749-40dc-b5fe-520dca37cef3)



Rotary Encoder:

![PXL_20231022_182947980](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/4a651d8d-e7ca-459f-bef7-8501918c5ad1)

![Merged_document(3)](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/81f5473c-a2da-41df-af5c-dc6c8649cfc8)







