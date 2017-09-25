# **Finding Lane Lines on the Road** 

## Problem Statement and Solution

### Goal

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road in a video file
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./PipelineImage/solidWhiteRight.jpg "InputImage"

[//]: # (Image References)

[image2]: ./PipelineImage/gray.jpg "Grayscale"

[//]: # (Image References)

[image3]: ./PipelineImage/gBlur.jpg "Grayscale"

[//]: # (Image References)

[image4]: ./PipelineImage/cEdges.jpg "Grayscale"

[//]: # (Image References)

[image5]: ./PipelineImage/masked_cEdges.jpg "Grayscale"

[//]: # (Image References)

[image6]: ./PipelineImage/hLines.jpg "InputImage"

[//]: # (Image References)

[image7]: ./PipelineImage/line_image.jpg "InputImage"


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. TO illustrate it with an example, let us consider the following input image (a single frame of input video)

![alt text][image1]


1) Convert the image to grayscale

![alt text][image2]


2)Apply Gaussian blur on the grayscale image

![alt text][image3]


3)Apply Edge Detector (Canny in this solution) to get the edges in the image

![alt text][image4]


4)Apply a polygonal mask to retain edges in the ROI and discard edges putside the region

![alt text][image5]


5) Apply Hough Transform to get the lane lines (edge detector points that are collinear). In case the road lanes are segmented, get a single extrapolated line by polyfit()

![alt text][image6]


6)Merge the detected lane lines from step 5 on the original image

![alt text][image7]



In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:

    1) Discard line segments whose absolute slope is less than a threshold.   
    
    2) Separating line segments by their slope to decide which segments are part of the left line vs. the right line.
    
    3) Finally applying polyFit of order 1 to them and Extrapolate to the top and bottom of the lane masking poygon


### 2. Identify potential shortcomings with your current pipeline


The potential shortcoming would be what would happen when 
1) There are multiple edges near the actual lanes
2) Vechicle moves on a road that has slope, where the camera will either point upwards or downwards
3) The road is not straight.



### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...


# RoadLaneDetection
