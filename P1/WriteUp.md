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
  7. Combine the original image with my Hough version.
    
    
    
    
    ![alt text][image7]


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by adding a check to see if the slope of the Hough line was positive of negative and within a certain slope range (0.55 to 0.85 for Right Lane & -0.55 to -0.85 for Left Lane). I had a bunch of random values that this helped toss out. If the slope was positive and within range I grabbed all of the values (x1, x2, y1, and y2) and put them into x and y arrays. I then used the polyfit 1st order function to give me a slope and y-intercept. Using the max and min Y values for the image, I found the x1 and x2 for the polyfit line and then drew it. It is a very crude method.


###2. Shortcomings with my current Pipeline
The shortcomings with this current Pipeline would fill up hours and hours of time to discuss. So I will just highlight the really terrible ones.
  1. It can't handle curves of any sort. The way I am using slope assumes straight lines that bend out toward the bottom of the screen. Curves do not always have this characteristic.
  2. There isn't any error handling built in. If I get slopes that don't fall into my range, I simply do not draw the line. You can see this in my videos as the line flickers.
  3. Not dynamic. If the screen size changes or lane position in the camera changes drastically, the program will suffer greatly.
  4. View the 'Extra' video.
  5. Poor coding. I have 'magic values', poor names, and all sorts of things that need to be cleaned up. I am coming from the PLC land and, what I do looks not so hot.
  6. My inexperience with what CV and Python offer are probably killing me. I know that there are better and easier ways to do what I am doing.
     
  
###3. Suggest possible improvements to your pipeline
The possible improvements would be to fix all of the shortcomings above. The left/right lane draw function needs to be entirely re-thought to allow for curves to be drawn well. Using slopes that are positive and negative and then assigning them a left or right is not good enough. I think I need to look at the left and right sides of the lane separately by doing two masks instead of one and then go from there. CV and Python do so much, that was unexpected. I need to also get better with the parameters for Canny and Hough. I plan on finding a 'tuning' guide.
