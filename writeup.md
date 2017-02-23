
---
**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied Gaussain smoothing, after that I found line edges with the Canny edge detection algorithm. To limit the search for lines first we defined our region of interest mostly in the lower half part of the image and masked the rest. On the masked image we ran Hough Transform to find the lines from the edges. The result was overlayed over the original sequence of images (viadeo stream). 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by computing the slopes of the lines and sorting out left and right lines based on the computed slope sign and threshold. After that average positions of left and right lines were computed separately. Both lines were then added to the line image.

Bellow are illustrations of the pipeline: 


###2. Identify potential shortcomings with your current pipeline


There could be many shortcoming of this pipeline exist. One shortcoming is clearly seen in the challenge video when the yellow line on the bright asphalt is nearly disappearing. The other problem is when lines are nearly vanished and cannot be detected on one side. Shadows introduce unpleasant contrast that also makes the line detecetion unrealiable. Direct sunlight into the camera I can imagine can create a lot of difficulties. 


###3. Suggest possible improvements to your pipeline

Possible improvements apart from parameters tuning would be maintaining a predictive estimate over the lines positions (e.g., Kalman Filter), better image processing, especially for yellow lines that can be at least color substituded by white. 