# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

## Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consists of the following steps: 
1. I converted the images to grayscale
1. I performed a guassian blur to reduce noise
1. I used the canny edge detection to create an edge map
1. I masked the lines using the region_of_interest function
1. I performed the hough transform to identify lines

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:
1. I divide lines based on which horizontal half of the screen they're on
1. I also filter for either positive / negative slopes I would assume lanes on that half of the screen would have
1. I then average each lane's lines' slopes and intercepts, both weighted against the line's distance
1. While averaging, I also retain the last 40 trailing points from previous frames to assist in the smoothing

### 2. Identify potential shortcomings with your current pipeline

A few potential shortcomings:
* If anything (eg: cars) were to block the lanes, the hough lines from the car would wrap my lanes lines
* If lanes disappear or are few and far between
* If the lanes start to curve, I will battle to detect (I only work with straight lines at the moment)

### 3. Suggest possible improvements to your pipeline

Possible improvements would be to:
* leverage linear regression or any other numerical method designed for extrapolation
* Instead to support extrapolation that supports curved or straight lines
