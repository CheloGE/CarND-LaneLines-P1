# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

* The goals of this project is to Make a pipeline that finds lane lines on the road


[//]: # (Image References)

[image1]: ./test_images/init_image.PNG "Grayscale"
[image2]: ./test_images/gauss_image.PNG "Gauss_smooth"
[image3]: ./test_images/canny_detector.PNG "canny_detector"
[image4]: ./test_images/trapezoildal_mask.PNG "trapezoidal_mask"
[image5]: ./test_images/hough_lines_extrapolated.PNG "hough_lines"
[image6]: ./test_images/final_image.PNG "extrapolated_lines"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 main steps:

1. Changing image to gray to apply algorithms into a one-channel image

![alt text][image1]

2. Gaussian smoothing to remove possible noisy pixels

![alt text][image2]

3. Applying canny edge detection to find boundaries in the image (1:2 threshold ratio applied)

![alt text][image3]

4. Masking the image with a trapezoidal mask.

![alt text][image4]

5. Getting lines through the Hough space

![alt text][image5]

6. Extrapolating lane lines to display them on the road frames

![alt text][image6]



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be in the extrapolation state which is being done by dividing the lanes based on the center of the frame. i.e. The vertical center of the image defines when the line lane detected is from the left or from the right. The problem with this approach would be in prominent curves where the center of the screen would not necessarily be defined by the center of the frame.


### 3. Suggest possible improvements to your pipeline

* A possible improvement would be to extrapolate lines independently of where they are located in the frame. i.e. lane lines should be extrapolated either if they are a left lane line or a right lane line.                             

* Another potential improvement could be to enhance the mask being used so that the algorithm doesn't confuse other lines outside the region of interest.

* Another improvement could be to fine-tune the parameters in the pipeline with an automatic technique such as a grid search.
