# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

* The goals of this project is to Make a pipeline that finds lane lines on the road


[//]: # (Image References)

[image1]: ./test_images/init_image.PNG "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 main steps:

1. Changing image to gray to apply algorithms into a one-channel image

![alt text][image1]

2. Gaussian smoothing to remove possible noisy pixels
3. Applying canny edge detection to find boundaries in the image (1:2 threshold ratio applied)
4. Masking the image with a trapezoidal mask.
5. Getting lines through the Hough space
6. Extrapolating lane lines to display them on the road frames




### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
