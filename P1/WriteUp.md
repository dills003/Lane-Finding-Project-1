#**Finding Lane Lines on the Road - Project #1** 

##Writeup For Project #1

###The following is how my first experience with lane finding went.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* The road is straight
* Curves are rough
[//]: # (Image References)  
[image1]: ./pipeline/pipe1.jpg "Grayscale"
[image2]: ./pipeline/pipe2.jpg "Grayscale Blurred"
[image3]: ./pipeline/pipe3.jpg "Canny"
[image4]: ./pipeline/pipe4.jpg "Canny Blurred"
[image5]: ./pipeline/pipe5.jpg "Canny Blurred Masked"
[image6]: ./pipeline/pipe6.jpg "Hough Lines"
[image7]: ./pipeline/pipe7.jpg "Combined"
---

### Reflection

###1. My Pipeline.

To be honest, this was the very first time I have ever used the term 'pipeline' to mean one part of code flowing into the next. I am new to all of this; Python, Git, Jupyter, CV, etc. So this has been quite the awesome learning experience for me.
My Pipeline Steps:
  1. Convert the image to grayscale. This makes the imaging processing less intensive.
    ![alt text][image1]
  2. Blur the Grayscaled image. This helps with making some of the edges smoother and easier to detect.
    ![alt text][image2]
  3. Apply the Canny edge finder function. This creates lines of where the function found an edge.
    ![alt text][image3]
  4. Smooth out the Canny edges. This felt like it helped with the Hough lines, but I was changing so many parameters, I am not sure if   it did.  
    ![alt text][image4]
  5. Mask the region of interest. Since I am only interested in the lane lines, I get rid of all of the extra stuff.  
    ![alt text][image5]
  6. Find the Hough lines and draw them. Apply the Hough function to find lines based on votes and draw them.
    ![alt text][image6]  
  7. Combine the orignal image with my Hough version.
    ![alt text][image7]


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by adding a check to see if the slope of the Hough line was positive of negative and within a certain slope range (0.55-0.8



###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
