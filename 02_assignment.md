---
title: 02_assignment
layout: default
---

# **3D print design that combines multiple parts**



## **Designing and 3D printing a watermill:**

### **Watermill definition:**
A watermill is a structure, builded as usual close to a river or a stream, which takes advantage of the kinetic energy of flowing water. The flowing water rotates the watermill and mechanical energy is generated. A watermill can be therefore used to produce electricity or other various tasks. 

The structure created for this project consists of two towers, a wheel with paddles along its outer edge, a long and narrow axle bar, and two stainless steel ball bearings. The design and construction of the watermill will involve utilizing the Fusion360 software program, the Bambu slicer application, and a Bambu X1 Carbon 3D printer.

## **CAD progress:**

## **First Iteration: Fig 1**

### **First Tower**
As previously stated, Fusion360 was utilized to design the structure of the watermill. To begin with, I created a rectangular shape (35mm x 60mm) on the XY plane. Then, the extrude command was used to elevate the rectangular shape by 20mm. The base of the tower was then designed and I had to design another structure on the top of the base. Using the same way, I created yet another rectangular shape (10mm x 35mm) on the XY plane. The only difference was that this second rectangular was positioned atop of the tower base. The extrude command was used again to lift the rectangular by 50mm. At this point, the whole tower was completed. 

### **Bearing cavity:**
In order to design the bearing cavity, I created a new sketch on the XZ plane and marked the outer surface of the tower on that plane. Next, a circle with a diameter of 16mm and a depth of 12mm was created at the center of the tower. This cavity was crucial to the whole design as it will hold in place the stainless steel ball bearing that will allow the rotation of the watermill wheel.

### **Second Tower:**
The second tower of the whole structure was created by using the mirror command, which creates a copy of faces, bodies, features, and components and mirrors them across a plane. In other words, the second tower was an identical copy of the first.

### **Watermill wheel:**
To create the watermill wheel, which had to lie between the two towers, I initially constructed a midplane along the XZ plane. This midplane creates a construction plane between two faces or work planes, in this case, between the two cavities that will host the ball bearings. 

Subsequently, I designed a 60mm diameter circle that uses as its center the very center of the two aforementioned cavities. At the same time a smaller circle with a diameter of 16mm with the same center was designed, which would act as whole within the wheel. 

Once again, the extrude command was used to give depth to the 60mm diameter circle. I used the symmetric configuration on the direction field and a distance of 10mm, meaning that the total length of the wheel would be 20mm. 

Finally, the paddles along the wheel’s outer edge were constructed. To design them, I sketched two closed irregular shapes, the first on the one side of the wheel and the second on the other, and I used the loft command to cut through the wheel.

### **Axle Bar:**
To create the axle bar I designed a circle with a diameter of 16mm atop of the midplane, which ‘slices’ the wheel right at the middle. Furthermore, I used the extrude command choosing again the symmetric configuration and a distance of 34mm. This meant that the axle bar was going through the wheel and inside the two cavities of the towers. 

Lastly, I created two 5mm in length cylinders with a diameter of 5mm. Those two cylinders were attached on both ends of the axle bar and were to be inserted in the ball bearings. That was one the most important features of the design as those two cylinders connect the axle bar and the wheel to the bearings and the towers.


### **Rounding the edges:**
The final stage in completing the structure's design involved rounding its corners. To do that, I used the fillet command and the setback corner type configuration. The radius value, which represents the degree of rounding, was set to be 1mm. 

![firsrt print evolution](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/037d64bf-5d35-4e23-826f-8dc005e112ae)
Figure 1: Shows the evolution of the initial watermill’s design using the Fusion360 program.


## **Second iteration: Fig 2**

The idea behind the second design of the watermill was almost identical with the first one described above but with a few corrections. The nature and the reason for some of those corrections will be further discussed in the next session. 

### **First tower:**
The design for the base and the tower remained the same as in the first iteration. The only distinction was their dimensions where the new base and tower are slightly larger measuring (40mm x 70mm x 20mm) and (20mm x 40mm x 60mm) respectively.

### **Bearing cavity:**
The bearing cavity was created in the same manner as in the initial iteration. This time, a circle with a diameter of 16mm and a depth of 5mm instead of 12mm was created at the center of the tower.

### **Second Tower:**
The second tower of the whole structure was created by using the mirror command.

### **Rounding the edges:**
The radius value to round the edges in the second iteration was set to be 2mm. The chosen corner type configuration was the setback one.

### **Watermill wheel:**
Initially, the XZ plane was constructed and was placed between the centers of the bearing cavities. The diameter and the thickness of the circle was 80mm and 30mm respectively.

To make room in the center of the wheel for the axle bar, I created a 10mm x 10mm rectangular-shaped hole by using the extrude command and the cut configuration, in contrast to the first iteration where the hole was circular.  

The paddles positioned along the outer rim of the wheel were constructed by following the same approach as before, namely, by using the loft command. The only difference was that I created two sketches using the 3-point arc and line commands , one on each side of the wheel, instead of just sketching two uneven surfaces as in the first iteration. 

### **Axle Bar:**
The axle bar was created in the same manner as in the first iteration. I used the extrude command, the symmetric configuration and a distance of 30mm. This meant that the axle bar was going through the wheel and measured a total of 60mm. On this occasion, the axle bar was placed differently, with a 5mm gap between it and the two tower cavities at both ends. 

Finally, two cylinders measuring 9mm each were attached on both ends of the axle bar. Those would connect the axle bar and the ball bearings.



![Second print evolution](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/cd2c0787-9cc1-4e75-bacd-6e7077a7fd24)
Figure 2: Shows the evolution of the second watermill’s design using the Fusion360 program.

## **Bambu Slicer set up:**

The configuration of the Bambu slicer was pretty straight forward, as most of the parameters were already set to their default values. It is worth mentioning that both iterations had the same slicer configurations. The only parameter that was manually changed or altered was the support parameter, which is responsible for generating support structures that are used for preventing overhangs or bridges to collapse during the 3D printing process (Fig 3). 

![blmbu slicer confi](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/5914e4c5-6375-44be-94a9-00a051f31698)
Figure 3: Values of the parameters, preparation, and preview of the upcoming 3D printed designs.

## **Three 3D print iterations:**

The watermill went through a total of three 3D printing iterations, with the first design being printed twice and the second one once. The first print started as normal but due to lack of glue on the thermal plate the process had to be halted . Despite the unsuccessful outcome, the 3D printer produced the bottom surfaces of the towers and the watermill wheel as depicted in Fig 4. 


![PXL_20230916_191924857](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/3b5b8d0a-f68c-4600-a610-a174a28af52c)
Figure 4: First 3D printing attempt of the watermill (First design).

The second attempted iteration was successful, however, the design had a major flow. The cylindrical axle was inserted inside the tower cavities and was after that connected to the bearings, meaning that the axle was rubbing against the inner walls of the cavities causing unwanted friction (Fig 5). This issue made the rotation of the watermill wheel almost impossible.   Thus, a second design and a third print was necessary. 


![PXL_20230916_192146265](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/97b71c14-85df-4e2f-9ccb-a187de6a6caa)
Figure 5: Second 3D printing attempt of the watermill (First design).

The third and final 3D printing attempt was also a success. On this occasion, it was the second design that was printed, as shown in Figure 6. In this case, no ‘negative’ issues were presented whatsoever. 


![PXL_20230916_192510791](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/3e4b901e-3bf2-4b09-87ac-afdae9fc3012)
Figure 6: Second 3D printing attempt of the watermill (Second design).

## **Discussion:**

Designing, slicing and 3D printing the windmill turned out to be a very enlightening experience which helped me understand more about how the Fusion360 software program works, as well as the Bambu slicer. 

Both the second and the third printed products function and perform more or less as they should. When placed beneath flowing water, the third printed watermill clearly outperforms the second one. The only thing missing is testing the rotations per minute (RPM) of the two watermills with a tachometer, which is unfortunately something I have not done yet. Despite the successful final print and the product’s good functionality, there is definitely room for improvement. 
