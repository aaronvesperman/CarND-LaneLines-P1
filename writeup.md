# **Finding Lane Lines on the Road** 

## Writeup by Aaron Vesperman



---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

[image2]: ./test_images_output/color_edges_solidWhiteCurve.jpg "color_edges"

[image3]: ./test_images_output/line_image_solidWhiteCurve.jpg "line segments"

[image4]: ./test_images_output/line_extended_image_solidWhiteCurve.jpg "line extended"

[image5]: ./test_images_output/solidWhiteCurve.jpg "color image"


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 9 steps. First, I converted the images to grayscale, then I applied Gaussian smoothing to blur grayscale image and found Canny edges.

![alt text][image2]

Next I created masked edges polygon, deteted straight line edges. 

![alt text][image3]

Next I created another masked edges polygon to connect/average/extrapolate into right and left lane lines. 

![alt text][image4

Finally I drew the left and right lanes lines on the original image.

![alt text][image5]


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by finding the slope of each line segment and then finding the average positive slopes and negative slopes (left and right respectively).

I also filtered out line segments that where outside the expected slope ranges.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when car is driving on cement or dirt roads instead of blacktop. Edges may be difficult to find. 

Another shortcoming could be traffic circles or very tight, slow speed turns due to slope filtering logic I added when drawing lane lines.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to detect the horizon to determine best region to process.

Another potential improvement could be to use more feedback/history to correct errors.

