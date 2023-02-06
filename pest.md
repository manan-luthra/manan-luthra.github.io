[About Me |](index.md) 
[ Education |](edu.md)
[ Projects |](projects.md)
[ Academic Publications |](publications.md)
[ Contact Info](contact.md)


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

(Note: The PIR sensor has a deep sleep issue)

## Detection using a pretrained model
Steps done:
1. Set up Ubuntu for Computer Vision
2. Installed Darknet, OpenCV and CUDA (for GPU computation)
3. Tested Darknet using a pretrained model
4. Used the Google Open Image Dataset (https://storage.googleapis.com/openimages/web/index.html) to download images for class "Insects"
6. Combined the images and the csv files in a single folder using the OIDv4 Downloader from the github repo (https://github.com/theAIGuysCode/OIDv4_ToolKit.git)
8. Created a custom config file
    For training, set batch and subdivision to 64
    Changed height and width to 420
    max_batches = 2000* no. of classes (4000 minimum)
    steps = 80% of max batches, 90% of max batches <br />
    
    ![Screenshot 2022-12-06 142611](https://user-images.githubusercontent.com/105019328/206026636-b8281bc6-3a91-476e-9fc8-5af42b720830.jpg)

  Updated the number of classes to 1 
    Changed filter to (class+5)*3=18
    Set all random=0
9. Next, created .txt file for all the image dataset. 
    Run this in cmd:
    python generate_train.py

    (Training might take hours)

12. Once the training was complete, used the darknet detector to test random images 

13. Once the prediction pops up, it's time for comiling the code for ESP32 on Arduino IDE

## Executing the ESP32 code on Arduino IDE


## Set up a Google Drive API 
1. Follow the steps in the link to set up a Google Drive API (https://how2electronics.com/how-to-send-esp32-cam-captured-image-to-google-drive/)
2. Make sure to enable the API and download the json file (store it where the original python file is)
3. Copy the location of the drive folder in which you want to save the images 


## OpenCV 
1. Open Visual Studio Code
2. Use the python code provided in the repo
3. Once you upload the code to the ESP32, open the serial port and copy the server URL 
4. Paste that in the "url=" codeline in the python code provided
5. Replace the path to the Google Drive folder, the weight file, the config file and the labels file <br />
![Screenshot 2022-12-06 140243](https://user-images.githubusercontent.com/105019328/206022347-9a52d914-f089-4009-890f-ddad313c63c8.jpg)


Run the code and the images should update in your Google Drive Folder 

<img src="https://user-images.githubusercontent.com/105019328/216864662-800f9512-6581-4fae-9379-a2af66407f2f.png">


