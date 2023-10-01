---
title: 03_assignment
layout: default
---

# **Laser cut a box with finger joints**

In this fourth assignment, the task was to laser-cut wooden pieces and build a 6-side parametric box. To assemble the parts that create the box, finger joints were designed at the edges of the wooden pieces. The whole point of the finger joints is to hold the box together instead of glue, screws, etc. 


## ** Fusion360 design** 

### **Bottom side of the parametric box**

The parametric box was designed using Fusion360 (Figure 1, blue panel), and the size of the box was top decided to be 45mm x 45mm x 45mm, making the box a perfect square. Initially, I designed the bottom part of the box. I used the center rectangle function and selected the origin point as my center in the XY plane. Then, it was time for the finger joints, and the first step was to mark out the cuts. I created four identical  rectangles along the north and west inward side of the sketch, measuring 6mm x 3mm. After that, I used the mirror command to mirror the rectangles to the south and east sides of the sketch. As mentioned above, the dimensions of the 2D bottom part were 45mm x 45mm. After designing the bottom part, I used the extrude command to give ‘’height’’ to the bottom sketch by 3mm.

![parametric box ](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/555c3046-786c-4f29-960c-1b27ed906574)
Figure 1: Shows the design of the bottom (blue shaded area) and the side panel (gray area) of the parametric box in Fusion360.


### **One of the sides of the parametric box**

The side panels of the wooden parametric box were designed to have a male end with two pins (east) and a female end with two cuts (west), as depicted in Figure 2 (second panel). In this case, I only had to design one side panel and laser cut it four times, as depicted in Figure 1 (gray panel). I started by designing a 45mm x 45mm rectangle on an offset YZ plane. In addition to the east-west pins, I designed four rectangles at the southern end of this new sketch. Those four new rectangles would bring forward the three pins to connect the side panels to the bottom panel. In the same manner as above, I mirrored those rectangles to the north side of the panel. To summarize, the side panels were to be laser cut four times and the bottom panel twice, as the side panels would fit with each other and the bottom and top panel.


Figure 2: End result of the laser cut process.

### **Offset value**


Now that the design was finished, I had to take into account the offset value in order to compensate for the laser's beam width. Offsetting the design by adding a few hundred of millimeters should not be an issue, but not in this case. Normally, when offsetting a sketch, a single click is enough to select all the lines or curves of interest, which was something that I missed. In other words, I used the offset command and selected only one line, instead of the whole sketch, meaning that the laser cut was inconsistent. Max did a valiant effort to find the problem, which was eventually solved and we managed to laser cut all the parts. The offset value was to be 0.2mm. Finally, all the parts fitted very well together and the box looks still robust and intact. The completed parametric box is depicted in Figure 3.


Shoutout to Max for being extremely helpful throughout the whole process!

### **Reflection**

The precision and speed that the laser cutting technology provides is extremely useful as it offers high quality cuts in a very short time. This technology could be also used to add in my floating buoy project. I could potentially laser cut a wooden or plastic piece to act as a removable base or structure of the instruments located inside the buoy, making the removing process of the instruments quicker.
