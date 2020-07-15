## Introduction


The traditional and preferred method for quantifying microbe populations is by colony enumeration. This process involves serially diluting liquefied samples, plating the samples on media plates, and counting the resulting colony-forming units. Assuming each colony-forming unit originates from a single microbe, the number of microbes can then be back-calculated 

Research technicians typically count the number of colonies by hand, which can number up towards hundreds on a plate. The task of counting is tedious and prone to error. To reduce this burden, we aim to develop a program to digitally enumerate the number of colony-forming units using images of the sampled media plates.

![image](images/github-image.jpg)

## Dataset

The dataset consists of two groups, training data, and testing data. The training dataset was generated via a colony-plate image generator. Colony variables that were tuned include the radius, x position, and y position. Radiuses were generated along a standard normal distribution to best emulate real data. The data set used to test the program consists of 32 real plate images taken at a group member’s lab. 

| Real plate image | Generated image |
| --- | --- |
| ![image](images/generated_images.jpg | width="100") | ![image](images/real_image.png | width="100") |


## Preprocessing

The testing data is pre-processed in 3 steps to simplify features. 

(1).  Convert each image to binary to create a clear distinction between the plate and colony pixels. We used Otsu’s method to determine the optimal threshold value for each image.

(2).  Remove the petri dish perimeter so that only the microbe colonies appear in the foreground (white). Connected units of white pixels that exceeded a certain size in proportion to the image size were classified as the petri-dish pixels and removed from the final output via masking

(3).  Resize all images to a standard 400 x 400 pixels in order to run the algorithm under a reasonable time constraint. The computer generated images in the training set do not need to be pre-processed since they were created in the proper format to begin with. 

| Real plate image | Binary image | Binary image without petri|
| --- | --- | --- |
| ![image](images/petri.png) | ![image](images/petri2.png) |![image](images/petri3.png) |


## Methods

We will preprocess our dataset (3) to contrast the background and colonies and remove noise. We will then develop a support vector machine to classify each pixel in the image as either part of the background or a colony. From our preprocessed data, we will attempt two methods to quantify the number of colonies: 

     (i) A clustering algorithm where the number of clusters equals the number of bacteria colonies 
     
     (ii) Using convolution neural networks for more robust results that can potentially support more edge cases. CNNs can potentially extract features not observed in the other methods, which can be combined through ensemble learning such as boosting. Finally, we'll analyze which algorithms provide effective results and then combine them using boosting methods. 

## Potentional Results

We aim to have a program that can count the number of colony forming units based on the images of sample media plates. One checkpoint we will have is to implement the support vector machine to classify each pixel in images by July 7th. 

