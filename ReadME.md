![image](https://github.com/adasun55/General-Electric-3D-Print/blob/master/image/bg.jpg)

# General Electric Metal 3D Printing Intelligence 
### *Developing predictive models to enhance the metal 3D printing process with sensor data* 

## Background 
Unlike the traditional manufacturing processes with forming and injection molding, additive manufacturing, also known as 3D printing, allows the creation of lighter, more complex, and economical designs that are too difficult or too expensive to build efficiently. 

## Collaboration
We have been working closely with **GE Additive**, the pioneering leader in additive design and manufacturing, and collaborating with UC Berkeley **Data-X** in order to increase manufacturing and operating efficiencies through explore improvements in metal 3D printing from a data science perspective. 

## Overall Approach
Our team has been working with the data that was generated through experiments from a GE Additive metal 3D printing machine. The dataset with characterization results and camera data was created by the printing laser and recorded by the photodiode sensor camera through an experiment that consisted of single line prints. There are two metal powder layers with different melt pools in single lines with blocks and strips division. The objective from GE is to build the best predictive model for melt pool dimension (width, depth, height, total height) forecasting. Our work will help to reduce parameter iteration time for new pieces from months to weeks, improving metal 3D printing processes accurately and effectively. Promising results will be tested further at GE Additive to validate experimental results.

## Dataset
1. Sensor data
There are data from 2 layers (161 and 181) with layer number at the end of the filename. Each layer has 2 files, one with .avi (camera data) and the other with .avi.tdms (tdms file which includes layer, x, y, APD, and LaserTTL). Each set of files has exact same length of records so that each image can be matched with the tdms file.

2. BoP02 Analysis KP_SCedit0306.csv
This data includes characterization results with corresponding block/strike IDs. 

3. How to connect sensor data to characterization
  * Data to be filtered out from sensor data
    * Non BoP data in each layer (16 block builds are included in each layer)
    * LaserTTL = 0

  * Assign Block ID: 
    * Please refer to block design.jpg. (Note that x, y is flipped in the sensor data). 141 includes block 15-22, and 161 includes 7-14. Characterization is        performed on 8 blocks.

  * Assign Strike ID in each block: assign strike ID 1 through 34 in each block

## Problem and Solution 
The first step taken was to take data from machine sensors, and a video feed of the laser focus point of the printing process. This helped to generate a single CSV file and frame images (we are taking frames at 30 fps and about 80,000 in total). After Exploratory Data Analysis (EDA) and Data Preprocessing, we built and trained various machine learning models on the data and evaluated the final performances. We chose the Random Forest model, which has the best accuracy among all. The 3rd step that the team implemented was to calculate more features from the images (using Sobel gradients), and exploring new approaches with autoencoders, a type of Neural Network. Our next steps would be to get more data from General Electric and to train the model on that data to improve its overall performance,then running the model on a few live prints and having General Electric validate the performance.




*Team: Ada Sun, Enrique Marin, Armyben Patel, Ziren Lin, Hassan Khawaja*
