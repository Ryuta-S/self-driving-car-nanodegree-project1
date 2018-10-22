# **Finding Lane Lines on the Road** 


---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road

**Example Input image**
![input](./test_images/whiteCarLaneSwitch.jpg)

**Example Output image**
![output](./test_images_output/whiteCarLaneSwitch.jpg)

---

### Reflection

### 1. I explain my pipleline

##### My pipeline consisted of 11 steps. 
First, I convert image to grayscale. Then, I use helper function 'grayscale()'.
![grayscale](./writeup_image/grayscale.jpg)

Second, in order to find yellow lane lines, convert image to hsv color space from rgb color space. And, using cv2.inRange() function, Find yellow area from hsv image. Then, example output image is below.
![yellow_color_mask](./writeup_image/yellow_color_mask.jpg)

Third, apply a color mask to grayscale image, judge it to be white when it is above the threshold vale, and find white lane. Then, the output image is below.
![white_color_mask](./writeup_image/white_color_mask.jpg)

Fourth, combine two images only extracted only white and only yellow, Using cv2.bitwise_or() function.Then, the output image is below.
![conbine_color_mask](./writeup_image/combine_color_mask.jpg)

Fifth, combine color mask image and grayscale image. The output iamge is below.
![conbine_gray](./writeup_image/combine_gray.jpg)

Next, apply gaussian blur to combine image.
![blur_gray](./writeup_image/blur_gray.jpg)

Next, apply canny edges detection.
![edges_gray](./writeup_image/edges_gray.jpg)

Next, region masking.
![masked_gray](./writeup_image/masked_gray.jpg)

Next, get lines-array using hough transform. And, divide into two arrays. The two arrays are divided depending wheter they belong to the left side or to the right side of the image.

Show the image in which the array having left lines is drawn.
![left_lines_only](./writeup_image/left_lines_only.jpg)

Show the image in which the array having right lines is drawn.
![right_lines_only](./writeup_image/right_lines_only.jpg)

Calculate a slope and intercept of the straight line from each array.
draw each line based on the slope and intercept.
This is the output image below.
![output](./test_images_output/whiteCarLaneSwitch.jpg)

### 2. Identify potential shortcomings with your current pipeline
1. It is easily affected by the weather. When the sun is strong, it becomes difficult to recognize the white line on the road. I recognize many points as edges. 
2. Cracks on the road are recognized as edges, and when taking slope, intercept and average, it becomes an outlier value.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to Perform histogram conversion to make it easier to find white lines.


