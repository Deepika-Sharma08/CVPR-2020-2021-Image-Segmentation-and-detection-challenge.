# CVPR-2020-2021-Image-Segmentation-and-Detection-challenge.
Lets' segment satellite earth images.



This is an open competition posted by CVPR 2020 & 2021] Agriculture-Vision Dataset, Prize Challenge and Workshop: A joint effort with many great collaborators to bring Agriculture and Computer Vision/AI communities together to benefit humanity! 
 Resources : 

www.agriculture-vision.com and https://github.com/SHI-Labs/Agriculture-Vision#download.

I have been working on this problem for a few months now and have tried various methods to solve this problem. The description of the problem is as follows:

The dataset used in this challenge is a subset of the Agriculture-Vision dataset. The challenge dataset contains 21,061 aerial farmland images captured throughout 2019 across the US. Each image consists of four 512x512 color channels, which are RGB and Near Infra-red (NIR). Each image also has a boundary map and a mask. The boundary map indicates the region of the farmland, and the mask indicates valid pixels in the image. Regions outside of either the boundary map or the mask are not evaluated.

This dataset contains six types of annotations: Cloud shadow, Double plant, Planter skip, Standing Water, Waterway and Weed cluster. These types of field anomalies have great impacts on the potential yield of farmlands, therefore it is extremely important to accurately locate them. In the Agriculture-Vision dataset, these six patterns are stored separately as binary masks due to potential overlaps between patterns. Users are free to decide how to use these annotations.

0 - background,  1 - cloud_shadow,  2 - double_plant,  3 - planter_skip,  4 - standing_water,  5 - waterway,  6 - weed_cluster

Sample images


      

      

      

      

      


  

  
No alt text provided for this image
Challenges

    Class imbalance.
    Poor resolution images.
    Class overlap.
    Most of the classes as double plant, weed cluster, waterway share similar features.

Resolutions

    Removed Planter skip from input data since the images for this class were too less for training.
    Filtered images which were poor resolution during pre-processing. Resulted number of images given for model training is 12,298 instead 12,901.
    For data preparation, I encoded each class with a unique prime number to ensure that each class is uniquely identified, even if classes overlap in image. For ex, if classes were encoded as 1,2,3,4,5,6 then summing all the images to create one annotated image for training would have entry for overlapped 1 and 5 and actual 6.
    Few more tricks: If classes overlapped, the sum of all the classes would not be one among numbers used for encoding, which is set([1,3,5,11,23,53]). So, I removed overlapping classes since the number of images with overlapping classes turned out to be too less. Re-encoded the classes as 1,2,3,4,5 such that num_of_classes could be input as 6 in the model, else model would pick maximum numeric available in an image as num of classes. 



 
