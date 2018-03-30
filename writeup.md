# **Finding Lane Lines on the Road** 

## Writeup

### In Order to make make self driving car software, comuter need to identify lanes on road.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Extrapolate Detected Lane lines


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[image2]: ./examples/canny.jpg "Canny Edges"
[image3]: ./examples/masked.jpg "Masked"
[image4]: ./examples/hough_lines.jpg "Hough Transform & Draw line"
[image5]: ./examples/weighted.jpg "Weighted image"


---

### Reflection

### 1. Description of pipeline. 

My pipeline consisted of 5 steps. 
> Step-1 : I converted the images to grayscale using helper funtion grayscale.

![alt text][image1]

> step-2 : Applied Gaussian blur on result image from step-1 using helper funtion gaussian_blur. Since raw grayscale image contains noise in image, its important to filter them out so rsult of further step is more robust.

> Step-3 : Applied the Canny transform on result of step-2 using helper function canny.

![alt text][image2]

> Step-4 : Masking region of interest using helper funtion region_of_interest .

![alt text][image3]

> Step-5 : Applied hough lines transform in order to identify straight lines using helper function hough_lines.

![alt text][image4]

> Step-6 : To draw line on original image weighted_img function applied.

![alt text][image5]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function and instead of drawing lines in this function i called extrapolate function to draw the lines.

extrapolate function usage linear regression by applying np.polyfit function on x and y coordinates. As result partial lines are displayed as complete lines.

Below are the steps used in extrapolate function : 

	step-1 : canculating slope of all lines
    step-2 : select right and left lines on basis of slope value and filter out unwanted lines on basis of slope threshold
    step-3 : separate x and y cordinates for both left and right lines
    step-4 : applying np.polyfit for regression
    step-5 : calculating x cordinates using y=mx+c
    step-6 : draw the lines



### 2. Identify potential shortcomings


One potential shortcoming would be what would happen when there is a turn on the road 

Another shortcoming could be when sharp changes in lightning condition causes problem

Rainy season can cause issue.


### 3. Suggest possible improvements 

A possible improvement would be to apply method to detect curve on road when ther is a turn.
