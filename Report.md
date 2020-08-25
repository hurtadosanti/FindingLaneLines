# **Finding Lane Lines on the Road** 

## Introduction

The goals of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection
The pipeline is defined in four(4) steps:
1. Read the image or frame
2. Highligh sections of interest by converting the image to hsv color space and find regions in the ranges:
    
        low_boundary=(0,0,200)
        high_boundary=(255,150,255)

3. Select the interest region to focus only on the road and remove other possible noise
4. Find the lanes lines using HoughLinesP and draw complete lines 

When higlightint the sections of interest the HSV color space is used which helps with not having problems between yellow and white lines, they are process equally.

To get the lines I use a naive aproach, of first separate lines by positive and negative slope. Afterwords, I average the slope, and intercept. To find the x,y values of the lines it is used the low and high numbers on the Y axis from the interest Region. Then, using the average slope and the average intercept, the X values are calculated.

![alt text][image1]

### 2. Identify potential shortcomings with your current pipeline
The issues with the actual solution are:
- Drawing the lines on the video is noisy, an option is to mantain the old points before each iteration, so if there is no point identified the line is not jumping.
- For the curves in the challenge video, the slopes can be restricted to a specific range so the lines do not cross
- Using vectorized solutions can contribute to better performance of the algorithm
- At present the region of interest is fixed, so if the horizon changes the algorithm could get confuse

### 3. Suggest possible improvements to your pipeline
The solution can be improve by removing the blue on the sky