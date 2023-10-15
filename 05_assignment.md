---
title: 05_assignment
layout: default
---


# **Final Project, Prototype 1:**


## **The project’s functionalities:**

As mentioned in my very first post on this webpage (00_assisnment), the primary function of the floating buoy will be the documentation of the wave height, which will be accomplished by measuring three degrees of acceleration and three degrees of gyroscopic motion, using the LSM6DS33 motion sensor. This sensor is directly mounted on the Feather nRF52840 Sense board that is to be utilized for this project. The Feather nRF52840 Sense board will be mounted inside the buoy’s 3D printed housing and powered using a Li-Po 3.7v battery. PLA plastic was used to 3D print the buoy’s housing. 

Another functionality of the buoy is the ability to recharge its battery using the energy of the waves. The goal here is to convert wave energy/mechanical energy into electrical power. Due to lack of knowledge in this field, I can firmly confess that I am short of ideas, however, by looking at some very interesting articles online, I discovered that it is possible to produce Alternating Current (AC) by passing a magnet through a copper wire. The AC production can be pivotal for the battery recharge function. Another idea is to produce AD by using a pendulum that will rotate around the x-axis. The pendulum will be mounted on a shaft and its rotation will trigger (rotate) a gearbox. The gearbox will be ‘’connected’’ to a generator by a smaller gear that is mounted to a shaft which is connected to the generator. This latter shaft will rotate and the generator will produce electricity by magnetic induction. 

Lastly, it is possible but difficult at the same time to calculate an approximate wind velocity by applying a Fourier Transformation on the slopes (downsides) of the wave height measurements spectrum. This calculation will provide a rather accurate estimation of the wind velocity without having an anemometer mounted on the buoy, meaning that this extra measurement comes with no additional costs and weight.

## **Components**

This project consists of a numerous amount of components, both electrical, physical, and electrical, as depicted in Figure 1.

* 3D printed Housing: Two hemispheres.
* 18 (M3) 3mm Ø x 40mm stainless steel bolts.
* 18 M3 nuts.
* 36 3mm Ø rubber O-rings. 
* 1 170mm Ø x 5mm rubber O-ring. *
* 1 205mm Ø x 5mm rubber O-ring. * 
* 1 piece of styrofoam. *
* 1 circle piece of laser-cutted plywood surface (150mm Ø x 3mm). *
* 1 stainless steel metallic shaft (8mm Ø x 140mm).
* 2 stainless steel ball bearings (8mm Ø).
* 1 3D printed pendulum. *
* 1 magnet. *
* Copper wire. *
* System that converts the wave/mechanical energy into electricity (Gearbox, gears, generator). *
* 1 Feather nRF52840 Sense board.
* 1 Li-Po 3.7v battery.
* 2 2mm Ø x 4mm screws.
(Parts marked with * are not in the Figure)


Figure 1: Depicts the 3D printed Housing, the bolts and nuts, the rubber O-rings that goes around the bolts and nuts, the metallic shaft and ball bearings, the Feather Sense board and the battery.

## **Housing**

As mentioned in the paragraph above, the buoy’s housing will primarily consist of the hemispheres measuring (200mm x 90mm). The whole design measures in total 220mm x 160mm. Since the buoy will be in direct and continuous contact with a water body, it needs to be completely watertight and waterproof. Therefore, it is important to add a layer of epoxy around the outside and inside surfaces of the housing. Additionally, rubber O-rings will be placed in places where cavities exist; e.g. screw holes. These measures intend to make the design withstand the extensive contact with water and to protect the electronics placed inside the buoy. 

## **Fabrication Technique**

Right at this point, I believe that the 3D print technique suits my project excellently. However, the buoy’s size and shape makes the printing time quite long (several hours). In addition, the build requires a lot of PLA plastic material, something that is not ideal at all. The piece of laser-cutted plywood surface will be used as a floor inside the buoy’s housing. The plan is to mound the sensor right atop of this surface. The advantage of the laser cutting technique in this case is the process's rapidness and low material consumption. 

## **Interaction with the sensors**

At this moment, I am still working on the script that will control the sensors and provide to me the wanted data. This script is currently being developed in the Arduino IDE environment and I upload it to the Feather nRF52840 Sense board via a usb cable. 

## **Lessons while building the prototype**

Creating this prototype provided valuable information and a deeper understanding about my own project as I faced several difficulties through the design process. I believe that the majority of those difficulties are now surpassed and the resulting prototype is a good approximation of the final design. Ideally, the size of the final product should be smaller and more compact (higher printing quality). That is to reduce the amount of PLA used and the printing time.




## **Missing hardware and software progression**

Although most of the project's physical components are now in place and ready to be assembled together, I am still missing the rotating pendulum as well as the components of the system that converts the wave/mechanical energy into electricity. In addition, I am still struggling to find the 2 O-rings that will be placed between the two hemispheres and will seal the whole build from water. 

When it comes to the software progression, I am working on the code that converts the acquired data from the sensor (acceleration data in 3 directions to displacement). This procedure is not as simple as I thought as there are a lot of parameters and assumptions that need to be carefully examined in order to get the best possible and accurate displacement (wave height) values. The main plan in this case is to finish with this script as soon as possible and begin to run a series of tests with the prototype to validate the sensor’s measurements. 

## **Next steps (Week 42-43)**

* Add an epoxy layer around the outsides and insides of the 3D printed prototype.
* Test whether the prototype is waterproof and watertight.
* Laser cut the base (floor) located inside the housing.
* 3D print a case for the Feather Sense board and the battery.
* Create the battery charger system and test it.
* Finish the code that controls the sensor.
* Store the data from the sensor in a SD card or monitor them live in an app.
* Assemble all the parts together and run tests.
* Find an instrument to charge the Li-Po battery with.
