[About Me |](/index.md) 
[ Projects |](/projects.md)
[ Education |](/edu.md)
[ Academic Publications |](/publications.md)
[ Contact Info](/contact.md)

## Breathing Sensory Feedback Device for Lung Transplants

### Abstract <br>
A digital spirometer is developed along with an application that introduces a certain level of gamification to the otherwise tedious practice. The immediate objective of this product is to engage the patients through gamification during their breathing sets and consequently improve their lung strength. 

### Clinical Relevance <br>
Spirometry is a breathing test that measures the amount of air that is inhaled or exhaled from the lungs. It also measures how easily and quickly this process can be carried out. A spirometry test can help diagnose COPD and asthma or check lung function before surgery. It also supports a patient in improving their lung muscles post-surgery to prevent the onset of pneumonia. The ability to practice spirometry is dependent on several factors. Post-surgery, the patient may experience exhaustion due to medications, chest pain while breathing, and a lack of motivation to exhaust themselves further with exercises. Since spirometry is a tedious and monotonous activity, patients often lose the zeal while carrying out their prescribed repetitions. In order to motivate patients to achieve their daily repetitions, an upgrade to the traditional spirometers is proposed in this project.

### System Design
The housing of the components is prototyped using additive manufacturing technology. The material used to prototype the casing is polylactic acid (PLA). The print has 0.1mm layer height with the top and bottom layers being 0.4mm in thickness. A triangular infill pattern was used to maximize structural strength at 40 percent infill.

<img src="https://user-images.githubusercontent.com/105019328/171053055-456172e3-ef08-4bb0-a4b7-3720348c7f5f.png" width="475" height="315">
<img src="https://user-images.githubusercontent.com/105019328/171053086-e65a3204-d522-442b-9ad1-f5c2b1f2eabc.png" width="475" height="400" style="text-align:right;">


### Components Used
>Adafruit MPRLS Pressure Sensor <br>
>ESP32S Microcontroller

### System Architecture
The architecture, as depicted below, is set up so that the ESP32s checks for Wi-Fi pairing when the device is turned on. It assesses the request and connects to a nearby Wi-Fi network. It starts accepting input from the pressure sensor once the serial connection is established. The sensor values decrease when the user inhales from the spirometer. These serial values are processed and sent to an asynchronous web server, which is then integrated into the project's gamification section.

<img src="https://user-images.githubusercontent.com/105019328/171053062-a649a865-1992-49eb-8a80-fa5f20d43944.png" width="800" height="700">


### Gamification
The game interface was designed using the Unity Real-Time Development platform. The game features a rigid body that moves between two points on the vertical axis, as shown. The distance moved and the direction of movement is dependent on the inputs received from the sensor. In this case, the direction of the vertical movement of a Rocket character is being used to differentiate between inhaling and exhaling. For the purpose of this prototype, the serial port was used to communicate between the microcontroller and Unity at a baud rate of 115200. This was also required to initialize the serial port in C#. Once the connection was established, an initial value was taken to determine the base pressure and threshold. If the pressure decreases or increases, the rocket moves upward or downward, respectively. To achieve this, the RigidBody 2D and the Box Collider functions from Unity were utilized. Multiple layers of background are added to provide a better sense of movement and progress.

<img src="https://user-images.githubusercontent.com/105019328/171053072-c5921f69-882f-45d8-b385-9b6e04763977.png" width="500" height="275">
<img src="https://user-images.githubusercontent.com/105019328/171053076-61e33c17-f37b-44db-a378-f62b1f8ff116.png" width="500" height="275">


### Check out this video:
<iframe width="560" height="315" src="https://www.youtube.com/embed/fn9fsPpiOmE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

