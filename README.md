# Face-Mask-Detection

## Overview
Face masks help reduce the transmission of SARS-CoV-2 by interfering with the spread of virus-laden droplets ejected from the nose and mouth. Wearing face mask is one of the precautionary steps an individual can take in order to lessen the spread of COVID-19. In this simple project, a video camera detects if an individual is wearing a face mask or not in real-time.
The detection steps looks somewhat like this: 

<img src="./Images/detection_step.png">

## Dataset
The dataset used to train the face-mask detection model taken from here.

This dataset contains 853 images belonging to the 3 classes, as well as their bounding boxes in the PASCAL VOC format. The classes are:

1. With mask
2. Without mask
3. Mask worn incorrectly

<img src="./Images/dataset.png">

Though the dataset is pretty imbalanced with most of the data belonging to With mask class, it works pertty well detecting With mask and Without mask classes. But more data for Mask worn incorrectly class is needed in order to detect this class properly.

## Workflow

1. Data preprocessing : All images have their bounding boxes in the PASCAL VOC format and their info saved in XML format in annotaions directory. Only the region bounded by bounding box taken as input and their respective labels taken as output.

2. Training mask detector model : Transfer learning was used to train the inputs. The classifier model was built with InceptionV3 neural network architecture. After training for 20 epochs, accuracy on test set was 96.81%.

3. Detecting face mask in real-time :First task was to detect faces from each frame of the video. At first I used Haarcascade classifer from OpenCV for face detection. Average FPS I got while running on my machine was around 16. But face detection wasn't that accurate. This classifer struggled detecting faces with mask. In low-light condition it struggled the most.
Then I tried MTCNN for face detection. This algorithm performed great detecting faces, even in the low light. But while running on my machine, the average FPS I got was about 1.4. Which is pretty slow comparing with haarcascade classifier.

## Results

**Input** | **Output**
------------ | -------------
<img src="./Images/results.jpg"> | <img src="./Images/result1.png">




