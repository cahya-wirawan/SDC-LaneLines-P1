# **Finding Lane Lines on the Road** 

## Writeup

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of following 6 steps:
- the images are converted to grayscale 
![grayscale_solidWhiteRight](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")
- the grayscale images are smoothed using gaussian blur function with kernel size of 5
![grayscale_blur_solidWhiteRight](test_images_output/grayscale_blur_solidWhiteRight.jpg)
- the canny function is used to detect the edges with low_threshold = 50 and high_threshold = 220
- masked specific region of the images since we want only to get the edges on this region
- hough_lines is used to find lines on this masked region and draw it
- then the original image is combined with the image from the last process (hough lines) 

The result is saved again as jpg file in output directory

In order to draw a single line on the left and right lanes, I modified the draw_lines() function with 
following steps:
- calculate the slope of each line
- if the slope is less than 0, then save the line in the left line array, otherwise in the right line array
- calculate the average of all left slopes and right slopes
- calculate the start and end of the left line using the average of left slopes
- calculate the start and end of the right line using the average of right slopes
- draw the left and right line calculated before



If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
