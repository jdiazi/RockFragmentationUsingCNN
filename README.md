# RockFragmentationUsingCNN

Our goal is to obtain the Fragmentation Curve of blasted rock images using Convolutional Neural Networks (CNN) through Image Segmentation ([Mask R-CNN](https://github.com/matterport/Mask_RCNN)).

Further research can be merged with geotechnical and operational criteria that lead to getting a Rock Fragmentation Analysis in a shorter time. Thus, mining operations could improve the accuracy of their operational KPI as Powder/Digging factor and so on.

## Overview

* Searched and downloaded muck pile images to create our dataset.
* Manual filtering of images considering their similarity with the operation.
* Generated segmentation masks for the whole image dataset.
* Prepared and augmented our image dataset.
* Trained and tested our model based on the Mask R-CNN architecture.
* Extract masks to develop the Rock Fragmentation curve.

# Workflow

## 1. Searching and downloading muck pile images

