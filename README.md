## Introduction


The traditional and preferred method for quantifying microbe populations is by colony enumeration. This process involves serially diluting liquefied samples, plating the samples on media plates, and counting the resulting colony-forming units. Assuming each colony-forming unit originates from a single microbe, the number of microbes can then be back-calculated 

(1).  Research technicians typically count the number of colonies by hand, which can number up towards hundreds on a plate. The task of counting is tedious and prone to error 

(2). To reduce this burden, we aim to develop a program to digitally enumerate the number of colony-forming units using images of the sampled media plates.

![alt text](http://url/to/img.png)

## Methods

We will preprocess our dataset (3) to contrast the background and colonies and remove noise. We will then develop a support vector machine to classify each pixel in the image as either part of the background or a colony. From our preprocessed data, we will attempt two methods to quantify the number of colonies: 

     (i) A clustering algorithm where the number of clusters equals the number of bacteria colonies 
     
     (ii) Using convolution neural networks for more robust results that can potentially support more edge cases. CNNs can potentially extract features not observed in the other methods, which can be combined through ensemble learning such as boosting. Finally, we'll analyze which algorithms provide effective results and then combine them using boosting methods. 

## Potentional Results

We aim to have a program that can count the number of colony forming units based on the images of sample media plates. One checkpoint we will have is to implement the support vector machine to classify each pixel in images by July 7th. 

