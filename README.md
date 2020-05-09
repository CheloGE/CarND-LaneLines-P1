# **Finding Lane Lines on the Road** 

---
## Summary
**Finding Lane Lines on the Road**

The goal of this project is to make a pipeline that finds lane lines on the road

### Dependencies
This project requires:

* [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit)

[//]: # (Image References)

[image1]: ./examples/init_image.PNG "Grayscale"
[image2]: ./examples/gauss_image.PNG "Gauss_smooth"
[image3]: ./examples/canny_detector.PNG "canny_detector"
[image4]: ./examples/trapezoildal_mask.PNG "trapezoidal_mask"
[image5]: ./examples/hough_lines_extrapolated.PNG "hough_lines"
[image6]: ./examples/final_image.PNG "extrapolated_lines"

---

### Reflection

### 1. Description of the pipeline implemented.

My pipeline consisted of 6 main steps:

1. Changing image to gray to apply techniques into a one-channel image rather than a 3-channel image.

![alt text][image1]

2. Gaussian smoothing to remove possible noisy pixels

![alt text][image2]

3. Applying canny edge detection to find boundaries in the image (1:2 threshold ratio applied)

![alt text][image3]

4. Masking the image with a trapezoidal mask. The mask was tuned visually, as shown below:

![alt text][image4]

5. Getting lines through the Hough space.

![alt text][image5]

6. Extrapolating lane lines to display them on the road frames. To achieve this the function draw_lines() were used differently. In fact, it was used twice, one for the left lane lines and one for the right lane lines. An example of the final result is shown below:

![alt text][image6]

The extrapolation step was done by averaging all slopes (avg_m) returned by the lines from the Hough space. Then, we do the same for the intercepts (avg_b) of the lines to finally get a single line described by the following equation:

  ```Y=avg_m*X+avg_b``` 
  
These lines create the points required by the ```draw_lines()``` function by getting their coordinates based on the bottom of the frame and the center of the frame "Y" values, as follows:

  ```Y1=bottom_of_the_frame_pixel```
  ```X1=(Y1-avg_b)/avg_m```
  
  ```Y2=center_of_the_frame_pixel```
  ```X2=(Y2-avg_b)/avg_m```

### 2. Identify potential shortcomings with my current pipeline


One potential shortcoming would be in the extrapolation state which is being done by dividing the lanes based on the center of the frame. i.e. The vertical center of the image defines when the line lane detected is from the left or from the right. The problem with this approach would be in prominent curves where the center of the screen would not necessarily be defined by the center of the frame.


### 3. Suggest possible improvements to my pipeline

* A possible improvement would be to extrapolate lines independently of where they are located in the frame. i.e. lane lines should be extrapolated either if they are a left lane line or a right lane line.                             

* Another potential improvement could be to enhance the mask being used so that the algorithm doesn't confuse other lines outside the region of interest.

* Another improvement could be to fine-tune the parameters in the pipeline with an automatic technique such as a grid search.
