# Self-Driving-Car--Lane-Tracking

# **Finding Lane Lines on the Road** 

The goal of this project is to make a pipeline that finds lanes on the road from camera video stream

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

This project performs lane detection in video streams using Python and OpenCV.

The pipeline consists of the following steps: 
* [1] Converting images to grayscale
* [2] Applying Gaussian smoothing
* [3] Applying Canny transform
* [4] Defining a polygon region mask and use that as region of interest for lane detection
* [5] Applying Hough transform, detect lanes and extend using extrapolation
* [6] Drawing transparent lanes on the original image
