# **Finding Lane Lines on the Road** 


**Finding Lane Lines on the Road**

The goal of this project is to make a pipeline that finds lanes on the road from camera video stream


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted the following steps: 
* [1] Converting images to grayscale
* [2] Applying Gaussian smoothing
* [3] Applying Canny transform
* [4] Defining a polygon region mask and use that as region of interest for lane detection
* [5] Applying Hough transform, detect lanes and extend using extrapolation
* [6] Drawing transparent lanes on the original image

In order to draw a single line on the left and right lanes, the draw_lines() function has been modified by:
* Isolating lines that belong to left and right lanes into separate stacks
* Applying linear regression to the points belonging to each lane stack
* Finding and removing the outliers among each stack after applying linear regression, in order to get more accurate, less noisy (chattery) lines
* Extending/extrapolating lines appropriately
* Finally overlaying transparent left and right lanes on the original image


![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


Some of the inherent shortcomings of the current approach can be summerized as:
* Parameters defined for Gaussian smoothing, Canny and Hough transforms are static and may not work under all lighting and environmental conditions
* Parts of the road lanes may get obscured or non existent and the algorithm may not be able to handle all edge cases
* The algorithm should be able to distinguish between lanes and what seems to be part of a lane (e.g. trash or spilled paint on the road), and that can vastly increase the complexity of this approach   


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to:
* Devise adaptability of the Gaussian smoothing, Canny and Hough transforms parameter so that they can change dynamically with the environment settings (characteristics of the input image)
* Use a supervised learing approach by implementing a neural net may obviate some of the current issues 
