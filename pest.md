[About Me |](/index.md) 
[ Projects |](/projects.md)
[ Education |](/edu.md)
[ Academic Publications |](/publications.md)
[ Contact Info](/contact.md)


# Smart Insect/Pest Detection System 
Pests are a huge threat to agriculture. According to a study by the Food and Agriculture Organization of the United Nations, pests destroy up to 40 percent of global crops annually. Each year, plant diseases cost the global economy over $220 billion, and invasive insects at least $70 billion. They tend to be the biggest threat to crop production. Early pest detection can reduce the loss in yield up to 40 percent. 

## Problem Statement 
The main goal of this project is to design a smart pest/insect detection system that uses computer vision to detect pests in an agricultural field. 

## Components Used:
LILYGO TTGO T-Camera ESP32 

## Specs:
Master chip: esp32 dual-core <br />
Protocol: Wi-Fi 802.11 b/g/n & Bluetooth 4.2 BLE & BR/EDR <br />
Flash: 4MB <br />
PSRAM: 8Mbytes <br />
Display chip: SSD1306 I2C <br />
Display type: OLED <br />
Display resolution: 128x64 <br />
PIR: AS312 <br />
Camera: OV2640 <br />
Camera resolution: 2 megapixels <br />

## Pin Configuration for TTGO ESP32:
#define PWDN_GPIO_NUM       -1 <br />
#define RESET_GPIO_NUM      -1 <br />
#define XCLK_GPIO_NUM       4 <br />
#define SIOD_GPIO_NUM       18 <br />
#define SIOC_GPIO_NUM       23 <br />
#define Y9_GPIO_NUM         36 <br />
#define Y8_GPIO_NUM         37 <br />
#define Y7_GPIO_NUM         38 <br />
#define Y6_GPIO_NUM         39 <br />
#define Y5_GPIO_NUM         35 <br />
#define Y4_GPIO_NUM         14 <br />
#define Y3_GPIO_NUM         13 <br />
#define Y2_GPIO_NUM         34 <br />
#define VSYNC_GPIO_NUM      5 <br />
#define HREF_GPIO_NUM       27 <br />
#define PCLK_GPIO_NUM       25 <br />

![image](https://user-images.githubusercontent.com/105019328/217409309-11c08ced-aa3e-4882-8bd0-e9b107194d1b.png)

(Note: The PIR sensor has a deep sleep issue)

## Training the YOLO model with custom images
- Trained YOLOv3 (a real time object detection system) on a custom dataset of insect images using Darknet (an open source neural network framework). 
- Used the Google Open Images Dataset v7 for downloading the image dataset for Insects. These images dataset had a .jpg file and a .txt file with the same name. Each line of the .txt file was of the format: <br>
<code>
<object-class> <x_center> <y_center> &lt;width&gt; &lt;height&gt;
</code>
- For using the YOLO detector, I converted the bounding box annotations to the required YOLO format. 

![image](https://user-images.githubusercontent.com/105019328/217408901-2094b4fb-8964-4d38-89d0-c68b57623677.png)
    
- Installed dependencies such as CUDA, CUDNN, OpenCV, in order to run the darknet executable file. Updated the config file and changed the filters and classes along with other configuration data. 
- For training purposes, the following changes were made:<br>
batch=64 <br>
Subdivisions = 64 <br>
Max_batches = 4000 <br>
steps= 1600, 1800

- Further, updated the line filters in the convolutional layers before the YOLO layer to: filters=(num_classes + 5)*3. Since, number of classes=1, filters=18
- After downloading the pretrained weights, I started the training. The weights were saved for every 1000 iterations. 

    
## Model testing
<img src="https://user-images.githubusercontent.com/105019328/216864662-800f9512-6581-4fae-9379-a2af66407f2f.png">

    
## Advantage of using YOLOv3 over classifier based systems:
- It looks at the whole image at test time so its predictions are informed by global context in the image. 
- It also makes predictions with a single network evaluation unlike systems like R-CNN which require thousands for a single image. This makes it extremely fast, more than 1000x faster than R-CNN and 100x faster than Fast R-CNN
    
## OpenCV and ESP32 integration
![image](https://user-images.githubusercontent.com/105019328/217409188-5f5b1c32-fc98-47e8-af40-d972d30470e6.png)


## Future works:
Using the neural network to classify the images of crop diseases and insect pests

