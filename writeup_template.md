#**Finding Lane Lines on the Road** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consists of 5 steps as below.:
*1) Turn the image into gray scale
*2) Give a gaussian blur to the image
*3) Conduct Canny Edge Detection algorithm on the image
*4) Put a mask (region of interest) on the image
*5) Make Hough lines 

Those were taken from previous courses, then I just tweaked the parameters a little.
Note that the tweaking procedure was from experiences.

In 5), draw_line is implemented, and the details like this:

Draw line:
*1) Find graidents and the average values of x1, y1, x2, y2 for the left and right side.
In doing so, I put if-statement that judges if the gradient is larger than 0 just like the hint says.
*2) Extrapolate the line by finding its expected points at the bottom and top with basic algebra
For the sake of argument, I assumed lanes in reality(and video) are linear.
With this assumption and basic algebra I calculated expected points of extrapolated lines.

###2. Identify potential shortcomings with your current pipeline:
*1) There are some abnormal lines sporadicaly in my result videos. My pipeline's average algorithm is not robust enough to screen anomalies from Hough transform.
*2) Also my pipeline functions only if the lines are straight enough. From the challange video, you can easily find many abnormal lines.
*3) Also my pipeline highly depends on parameters which are fixed. It should change in accordance with the surroundings.


###3. Suggest possible improvements to your pipeline:
*1) If the tweaking procedure is automatic then it will prevent the system from making many abnormal lines. Because the parameters are already fixed, it is not robust and causes shortcomings above mentioned.
*2) The same kind of improvement can be applied to the region of interest. If the region can adapt to lanes, then anomalies will decrease.
