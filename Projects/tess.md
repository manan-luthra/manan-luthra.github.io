[About Me |](/index.md) 
[ Education |](/edu.md)
[ Projects |](/projects.md)
[ Academic Publications |](/publications.md)
[ Contact Info](/contact.md)

## Origami based Tessellation Actuation 

Research Question

```
How can the directional stiffness exhibited by origami tessellations be used to simplify the actuation of the locomotion of a laminate robot?
```

Some origami tessellations such as the ‘snake skin’ tessellation exhibit an interesting property of directional stiffness. This means that as force is applied to the tessellation in one direction it easily flexes but when force is applied in the opposite direction the structure reaches a point at which it becomes rigid or stiff. This property could be used to allow for a work loop in a gait by only moving a limb forwards and backwards and allowing the directional stiffness to create the force difference needed for motion.


The research is tracatble, novel 


## Biomechanics Background and Initial Specifications 



## System Kinematics 

Our robot will be built of 4 identical legs. The diagram below shows how we specify several points, reference frames, and distances for one leg. The end stop is a conceptual model for the behavior of our leg design. The leg is made of a tessallation that is easily deformed in one direction but reaches a singularity when deformed in the oposite direction preventing futher motion in that direction. The leg joint is modeled with a spring and damper so it mimics the tessallation joint.

![image](https://user-images.githubusercontent.com/105019328/172065357-3af0c983-7bb4-4a4c-9dcf-35c8499c4469.png)

## System Dinamics 

Below is a diagram of how the points are defined for the whole robot assembley. The details for the definitions of each leg are not shown on this diragram as they similar to thouse in the above diagram and would clutter this diagram making it hard to understand. Note the robot body that is defined as a beam from point A to point B is free from the orign marked in the lower left corner. This diagram is a side veiw of the robot and BEF and BCD legs on the real robot are sperated in the z direction.

![image](https://user-images.githubusercontent.com/105019328/172067903-231cc1a3-6c00-4ac3-bb31-5f566645bb0f.png)


We are modeling the beams that make up the legs as ridgid links as our expirements showed that they are rigid untill failure due to buckling. This will not affect our locamtion strategy as we did not plan for link compliance to store energy during locomotion.

Naming conventions:
Legs:
-BCD leg 1
-BEF leg 2
-AGH leg 3
-AIJ leg 4
Leg tips are always the letter that comes later in aphebetical order. A and B are points on the body.
The beams connected to A or B are the first leg beams and the others are the leg second beams.


## Parameter Identification 

1. Buckling Test

This experiment aimed at determining whether our system buckles due to axial load. When assessing and designing structures, there are usually two main concerns: (1) the structure's ability to support a given load without experiencing excessive stress, and (2) the structure's ability to support a given load without incurring unacceptable deformation. In this experiment, the element to be tested is a single layer (laser cut) tesselation of the prototype. A setup was created using LEGOs which allowed me to put load on the leg and perform the test as shown in the image below.

![image](https://user-images.githubusercontent.com/105019328/172068985-0161f03d-9bfa-4135-b944-1cb5a22a66b4.png)

Here is the top base for the framed system which works like an axial slider:

![image](https://user-images.githubusercontent.com/105019328/172068995-eaead7a5-f7c2-4aff-b4b4-8c84d62fafe9.png)

![image](https://user-images.githubusercontent.com/105019328/172068999-20191fbc-d576-4390-a446-cc4bf5ad01dd.png)

The dimensions of the laser cut leg: 80.6mm x 22.5mm, thickness 3mm. On adding weight to the top base plate, I was able to deduce the maximum weight beyond which the leg buckles. The maximum buckling weight came out to be 423.1g 

![image](https://user-images.githubusercontent.com/105019328/172069011-359581a0-1135-4ff2-9508-d68385d6556d.png)


2. MAss and Inertia Properties 

This was a colaborative effort amongst the team members. My role was to take the computed mass and inertia values and modify our dynamics code to reach optimization. I considered experimenting on a single leg rather than the complete system and modified the values to obtain the following results:


3. Setup and Analysis of Damping setup using Tracker Physics software 

![image](https://user-images.githubusercontent.com/105019328/172069039-26800a2f-a5cc-449a-a6b9-72821ebd7854.png)

The above pictures show the experimental setup used in this test. Vice grips were used to hold the prototype leg. Two Weights of 45g each were attached to the bottom of the leg to promote damping. Blue markers were attached at mulitple positions for high visibility. Two reference points were taken at the back of the setup. A video was taken in slo motion and was evaluated using the Tracker (Physics) software.

![image](https://user-images.githubusercontent.com/105019328/172069044-273061a5-0c7e-403e-ae7b-eb52ee846345.png)

I began by selecting the frame length of the video to be evaluated by placing the black markers in position. Next, I added the coordinate axis and fit it according to the reference frame. I added a calibration stick to the markers on the prototype leg. This allowed me to autotrack the damping oscillations of the leg as a single mass. The output waveforms and values are shown as below.

![ezgif com-gif-maker (5)](https://user-images.githubusercontent.com/105019328/172069120-0a11d94f-c907-44f0-a5ed-476f82b324ec.gif)



