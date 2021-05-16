# Rock Fragmentation Curve using Mask R-CNN

Our goal is to obtain a Fragmentation Curve of blasted rock images based on a Semantic Segmentation Model supported by [Mask R-CNN](https://github.com/matterport/Mask_RCNN).

Further research can be merged with geotechnical and operational criteria that lead to getting a Rock Fragmentation Analysis in a shorter time. Thus, mining operations could improve the accuracy of their operational KPI as Powder/Digging factor and so on.

## Overview

* Searched and downloaded muck pile images to create our dataset.
* Manual filtering of images considering their similarity with the operation.
* Created a Training and Validation image dataset.
* Labeled images and created masks.
* Prepared and augmented our image dataset (pending).
* Trained and tested our model based on the Mask R-CNN architecture.
* Extract masks to develop the Rock Fragmentation curve.

## Workflow

### 1. Searching and downloading muck pile images from Google

<p align="center">
  <img src="https://github.com/jdiazi/RockFragmentationUsingCNN/blob/main/images/rockblastedimages.jpg">
</p>

### 2. Creating image datasets and labelling them

The training dataset consisted of 48 images, and the validation one of 12 images.

<p align="center">
  <img alt="Training set" src="https://github.com/jdiazi/RockFragmentationUsingCNN/blob/main/images/training_set_48_images.jpg" width="460" height="240">
&nbsp; &nbsp; &nbsp; &nbsp;
  <img alt="Validation set" src="https://github.com/jdiazi/RockFragmentationUsingCNN/blob/main/images/validation_set_12_images.jpg" width="460" height="240">
</p>

We used [VGG Image Annotator](https://www.robots.ox.ac.uk/~vgg/software/via/via-1.0.0.html) for the labelling process.

<p align="center">
  <img src="https://github.com/jdiazi/RockFragmentationUsingCNN/blob/main/images/imageSegmentationMask.jpg">
</p>


### 3. Image pre-processing

* Our main challenge when using rock blasted images from google is that we have to deal with image noise, distorsion by focal length, sunlight effect, etc. Currently, we are working on how to address this problem.
* So far, we get that in order to improve the metrics of our Semantic Segmentation Model, it is mandatory that it can recognize the borders of each rock.
* By using the Sobel algorithm, we get a good result, but again, we are looking for a more robust solution.

<p align="center">
  <img src="https://github.com/jdiazi/RockFragmentationUsingCNN/blob/main/images/imageSobel.jpg">
</p>

### 4. Training and validation process

As we said before, we used Mask R-CNN to train our model. Mainly because its easier to use for non-tech professionals.

When it comes to the score the model, results are better than expected but it is clear that there is still a lot of room for improvement (for the most part in the pre-processing stage)

<p align="center">
  <img src="https://github.com/jdiazi/RockFragmentationUsingCNN/blob/main/images/predictedImage.jpg">
</p>

### 5. Creating the Rock Fragmentation Curve

The fist step to create the Rock Fragmentation Curve is:
* Isolate the predicted masks from the picture.
* Count and calculate the area of each mask.
<p align="center">
  <img src="https://github.com/jdiazi/RockFragmentationUsingCNN/blob/main/images/maskIsolation.jpg">
</p>

* Get an equivalent diameter for each area obtained.
* Create an array containing all the diameters to plot then as a Histogram and then, as a Cummulative Density Plot.
<p align="center">
  <img alt="Rock size histogram" src="https://github.com/jdiazi/RockFragmentationUsingCNN/blob/main/images/rockSizeHistogram.jpg">
&nbsp; &nbsp; &nbsp; &nbsp;
  <img alt="Validation set" src="https://github.com/jdiazi/RockFragmentationUsingCNN/blob/main/images/granulometricCurve.jpg">
</p>

_**Note: Given that we are not working with a scale, we created a histogram based solely on pixel dimension.**_

## Next steps

* Improve the pre-processing stage.
* Apply data augmentation.
* Test our model in a real image dataset used by mining companies.

## References

* [Automated Image Segmentation and Analysis of Rock Piles in an Open-Pit Mine](https://www.diva-portal.org/smash/get/diva2:1010999/FULLTEXT01.pdf)
* [An Application of Deep Neural Networks for Segmentation of Microtomographic Images of Rock Samples](https://www.mdpi.com/2073-431X/8/4/72)
* [Estimation of particle size distribution on an industrial conveyor belt using image analysis and neural networks](https://www.sciencedirect.com/science/article/abs/pii/S0032591014003465)

## Acknowledgments

* [Mask RCNN](https://github.com/matterport/Mask_RCNN)
