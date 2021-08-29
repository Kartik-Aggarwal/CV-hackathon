# CV-hackathon

The repository contains 3 IPYNB files
* Yolov5
* Other_Approaches
* dataset_creater

Rest other are **utils** and **tools** which are used along the code

### **Yolov5.ipynb**
 * This file contains code to **main approach** used for detection
* *NOTE* It is **highly** recomended that you upload and execute this file on **Google Colab** only

### **Other_Approaches.ipynb**
* This code file contains 3 other Approaches which were practised along with main code

### **dataset_creater.ipynb**
* Extracting ROIs out of images and creating dataset manualy can be very tedious task
* This code file contains pragram to which make the process very easy
* All the usage instructions are commented inside the file

****All the 3 files are well commented and code instructions and usage of other files present in this repository is directed in them**

### **Final_results_csv_file**
This contains the **defect_box** and **defect_type** csv files

### **Presentation** 
This is uploaded as **AlphaQ.pptx**


## Approaches and Explanation

### 1. Using Morphological Operations
* It is observed that the defect has different texture than the fabric. This is the basis of this approach.
* Combination of Sobelx and Sobely operations are applied and binary thresholding is done. This seperated out the defect from the fabric.
The following figure shows the results\
!["1_1"](https://github.com/Kartik-Aggarwal/CV-hackathon/blob/master/readme_images/1_1.png)

* Borders of image contains noise, thus center portion of the frame is taken as ROI.
* Image is divided into rectangles and pixel intensity of each is noted. Region with highest pixel intensity is considered to the the defect.
The following image shows the same.
!["1_2](https://github.com/Kartik-Aggarwal/CV-hackathon/blob/master/readme_images/1_2.png)

Following are the results of this method.
!["1_3"](https://github.com/Kartik-Aggarwal/CV-hackathon/blob/master/readme_images/1_3.png)

### 2. Using Feature Matching

* Since all defects share a common texture which is different from the fabric, feature matching can be applied.
* Points in the image with features similar to the defects are returned 

!["2_1"](https://github.com/Kartik-Aggarwal/CV-hackathon/blob/master/readme_images/2_1.png)

### 3. Classification using Linear Binary Patterns (lbp)

* Again exploiting the advantage that defects are textured different from the fabric, we compute lbp
* That pattern is computed as local binary pattern and a histogram of patterns is formed. Then these histograms are fed to SVM Classifier for classification
* Then while testing, the input image is divided into several rectangular sections and each of which is fed into SVM clalssifier.
* The final ROI is taken as the intersection of all ROIs

Following image depects the same
![3_1](https://github.com/Kartik-Aggarwal/CV-hackathon/blob/master/readme_images/3_1.png)
