# Udacity Self-Driving Car Nanodegree - Finding Lane Lines on the Road
This repo contains the code written to complete the first project on Udacity Self-Driving Car Nanodegree. This project consists of algorithms to identify lane lines on the road on a video. The video is taken from a camera at the center of a vehicle. This code is able to identify yellow and while lane lines on road.

## Prerequisites
To run this project, you need [Miniconda](https://conda.io/miniconda.html) installed(Follow [instructions](https://conda.io/docs/install/quick.html) to quickly install)

## Installation
To create an environment for this project use the following command:
```
conda env create -f environment.yml
```
After the environment is created, it needs to be activated with the command:
```
source activate carnd-term1
```
and open the project's notebook P1.ipynb inside jupyter notebook:
```
jupyter notebook P1.ipynb
```

## Overview
The repo contains the jupyter notebook [P1.ipynb](/P1.ipynb) where the processing pipeline is implemented inside the function `detect_lanes`. The pipeline consists on six steps represented by six different functions which are called using functions:
1. Gray conversion : Returns a gray scaled version of the input image using cv2.cvtColor method.
2. Blur Image `gaussian_blur`: Applies a Gaussian blur to the provided image using cv2.GaussianBlur method.
3. Canny `canny`: Use a [Canny transformation](https://en.wikipedia.org/wiki/Canny_edge_detector) to find edges on the image using [cv2.Canny](https://docs.opencv.org/3.4.1/da/d22/tutorial_py_canny.html) method. 
4. Masking `region_of_interest`: Only keeping region where lane line are available (for now...).
5. Hough:Transform `hough_lines`: Use a [Hough transformation](https://en.wikipedia.org/wiki/Hough_transform) to find the lines on the masked image using [cv2.HoughLinesP](https://docs.opencv.org/3.0-beta/doc/py_tutorials/py_imgproc/py_houghlines/py_houghlines.html). Function `hough_lines` calls `draw_lines` which extrapolates detected segments of lines to create single lane line.
6. Weighted image `weighted_img`: Combining lane lines image and original image.


