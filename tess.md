[About Me |](/index.md) 
[ Projects |](/projects.md)
[ Education |](/edu.md)
[ Academic Publications |](/publications.md)
[ Contact Info](/contact.md)

## Origami-based Tessellation Actuation 

Research Question

```
How can the directional stiffness exhibited by origami tessellations be used to simplify the actuation of the locomotion of a laminate robot?
```

## Biomechanics Background and Initial Specifications 
Some origami tessellations such as the ‘snake skin’ tessellation exhibit an interesting property of directional stiffness. This means that as force is applied to the tessellation in one direction it easily flexes but when force is applied in the opposite direction the structure reaches a point at which it becomes rigid or stiff. This property could be used to allow for a work loop in a gait by only moving a limb forwards and backwards and allowing the directional stiffness to create the force difference needed for motion.


## System Kinematics 

Our robot is built of 4 identical legs. The diagram below shows how we specify several points, reference frames, and distances for one leg. The end stop is a conceptual model for the behavior of our leg design. The leg is made of a tessellation that is easily deformed in one direction but reaches a singularity when deformed in the opposite direction preventing further motion in that direction. The leg joint is modeled with a spring and damper so it mimics the tessellation joint.

<img src="https://user-images.githubusercontent.com/105019328/172065357-3af0c983-7bb4-4a4c-9dcf-35c8499c4469.png" height= "375" width= "500" >

## System Dynamics 

Below is a diagram of how different points are defined for the whole robot assembly. Note the robot body that is defined as a beam from point A to point B is free from the origin marked in the lower left corner. This diagram is a side view of the robot and BEF and BCD legs on the real robot are separated in the z direction.

<img src="https://user-images.githubusercontent.com/105019328/172067903-231cc1a3-6c00-4ac3-bb31-5f566645bb0f.png" height= "375" width= "500" >

![ezgif com-gif-maker (6)](https://user-images.githubusercontent.com/105019328/172069223-1d6f75e3-ae3c-49de-8da6-d0b207d904cc.gif)


We modelled the beams that make up the legs as rigid links (our experiments showed they are rigid until failure due to buckling). This will not affect our locomotion strategy as we did not plan for link compliance to store energy during locomotion.

**Naming conventions:** 
Legs: <br>
Leg 1: BCD <br>
Leg 2: BEF  <br>
Leg 3: AGH  <br>
Leg 4: AIJ <br>

## Tessellated Leg Design
<img src="https://user-images.githubusercontent.com/105019328/216862691-cf6e7ac2-5306-44ae-84a6-d55ff7cecc62.jpg" height= "375" width= "650" >
<img src="https://user-images.githubusercontent.com/105019328/216862699-5d7735fc-ba8f-41b7-9b0a-c169e66eabfd.jpg" height= "375" width= "650" >
<img src="https://user-images.githubusercontent.com/105019328/216862705-3f212155-597f-41fe-8a01-df5c4517ac91.jpg" height= "375" width= "650" >

## Parameter Identification 

- Buckling Test

This experiment aimed at determining whether our system buckles due to axial load. When assessing and designing structures, there are usually two main concerns: (1) the structure's ability to support a given load without experiencing excessive stress, and (2) the structure's ability to support a given load without incurring unacceptable deformation. In this experiment, the element to be tested is a single layer (laser cut) tessellation of the prototype. A setup was created using LEGOs which allowed us to put load on the leg and perform the test as shown in the image below.

<img src="https://user-images.githubusercontent.com/105019328/172068985-0161f03d-9bfa-4135-b944-1cb5a22a66b4.png" height= "600" width= "500" >


Here is the top base for the framed system which works like an axial slider:
<img src="https://user-images.githubusercontent.com/105019328/172068995-eaead7a5-f7c2-4aff-b4b4-8c84d62fafe9.png" height= "375" width= "500" >

<img src="https://user-images.githubusercontent.com/105019328/172068999-20191fbc-d576-4390-a446-cc4bf5ad01dd.png" height= "600" width= "500" >

The dimensions of the laser cut leg: 80.6mm x 22.5mm, thickness 3mm. <br> <br>
On adding weight to the top base plate, we were able to deduce the maximum weight beyond which the leg buckles. The maximum buckling weight came out to be 423.1g <br>
<img src="https://user-images.githubusercontent.com/105019328/172069011-359581a0-1135-4ff2-9508-d68385d6556d.png" height= "375" width= "500" >

- Mass and Inertia Properties 

This was a collaborative effort amongst the team members. We took the computed mass and inertia values, and modified our dynamics code to reach optimization. We considered experimenting on a single leg rather than the complete system and modified the values to obtain the results.

- Setup and Analysis of Damping setup using Tracker Physics software 

Tracker is a software application used in physics education to visualize and analyze motion. It is designed to help understand and explore the concepts of motion, velocity, and acceleration. It allows users to track the motion of an object and to perform measurements such as position, velocity, and acceleration. This software can be used to analyze real-world data or to create simulations of physical systems. 
<img src="https://user-images.githubusercontent.com/105019328/172069039-26800a2f-a5cc-449a-a6b9-72821ebd7854.png" height= "375" width= "500" >


The above images show the experimental setup used in this test. Vice grips were used to hold the prototype leg. Two weights of 45g each were attached to the bottom of the leg to promote damping. Blue markers were attached at multiple positions for high visibility. Two reference points were taken at the back of the setup. A video was taken in slow motion and was evaluated using the Tracker software.

![image](https://user-images.githubusercontent.com/105019328/172069044-273061a5-0c7e-403e-ae7b-eb52ee846345.png)

We selected the frame length of the video to be evaluated by placing the black markers in position. The coordinate axis was added and was fit according to the reference frame. We further added a calibration stick to the markers on the prototype leg. This allowed us to autotrack the damping oscillations of the leg as a single mass. The output waveforms and values are shown as below.

![ezgif com-gif-maker (5)](https://user-images.githubusercontent.com/105019328/172069120-0a11d94f-c907-44f0-a5ed-476f82b324ec.gif)

## Final Prototype
<img src="https://user-images.githubusercontent.com/105019328/216860184-d3f63f5c-d1ec-4865-912a-466dd23d0620.jpg" height= "375" width= "500" >
<img src="https://user-images.githubusercontent.com/105019328/216860221-1164e13f-68de-442e-a107-8f5619f3015c.jpg" height= "375" width= "500" >

## Origami Leg Movement to avoid obstacles:
<img src="https://user-images.githubusercontent.com/105019328/216863000-6ee5a128-41ec-444c-9b22-1001932d42ae.gif">

(_Note: clideo.com was used to convert the above video to slo-mo_)

