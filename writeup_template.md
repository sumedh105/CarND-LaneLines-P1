# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

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

My pipeline consits of the following steps:

1. Converting an input image read to the "grayscale image". This is done because, it is easy to apply the Canny edge
   detection on an image which has a single channel.

2. Applying "Gaussian blur" function to the gray scale image. This is done to smoothen the grayscale image. The Gaussian
   blur function removes any noise present in the image. The kernel size chosen by me is 13. I arrived at this kernel
   size by trial and error method.

3. Applying the "Canny edge" detection algorithm to the smoothened image from Gaussian blur. Apart from the image, the
   canny edge detection algorithm takes "low threshold" and "high threshold" as the parameters. All the pixels below low
   threshold are blackened out and all the pixels above high threshold are whitened. The low threshold and high
   threshold values chosen by me are 50 and 150 respectively.

4. On the output of canny edge detection, "region of interest" is chosen. The region of interest is the region where the
   lanes are there in the image. The region of interest chosen in my case happens to be a trapezoid. The co-oridnates
   are chosen once again on trial and error method.

5. Once the region of interest is chosen, Hough transform is applied on the image. Hough transform converts the point in
   an image to the Hough space. A point in in the image space is then a sinusoidal curve in the Hough space. Apart from
   rho and theta, the parameters passed to this function are threshold, max_line_length and max_line_gap. The values
   chosen for these parameters are 20, 40 and 200 respectively. These values are chose once again based on trial and
   error method.

6. The input and the output images are as shown below:

### 2. Identify potential shortcomings with your current pipeline

1. One potential short coming is, the lane lines in the challenge video are distorted. 


### 3. Suggest possible improvements to your pipeline

1. A possible improvement could be to calculate the slope in the draw lines function. Based on the slope value, the
   lines can be categorized into the left lane or the right lane.
