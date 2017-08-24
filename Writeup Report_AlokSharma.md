
**Finding Lane Lines on the Road**

The goals of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect/explain how the pipeline has been implemented - discuss its strengths and weaknesses
* How can the pipeline be improved


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Pipeline description
The pipeline I implemented is available in the process image method. It consists of following steps:
1. Convert input RGB image to Grayscale
2. Apply Gaussian blur to grayscale image. I chose kernel size = 3 for blurring
3. Use canny edge detection to detect edges in the image
3. Create and apply a mask that defines region of interest
4. Use a hough transform to detet and draw lane lines

In order to extend the detected lane lines from bottom to top of lane in the image I modified the draw_lines() function as explained below:

* Define 2 lists to store points: list_1 and list_2
* For each line segment:
    ```Calculate length and slope of segment using point1 and point2```
    ``` If length > 5 pixels and slope > 0
      `if x-coordinate of point1 > 0.5* width_image
        add point1 to list1
      if x-coordinate of point2 > 0.5* width_image
        add point2 to list1
    Else if length > 5 pixels and slope < 0 
      if x-coordinate of point1 < 0.5* width_image 
        add point1 to list2
      if x-coordinate of point2 < 0.5* width_image
        add point2 to list2```
 * Fit a polynomial of 1-degree to list1 and list2 using numpy's polyfit 
 * Using the polynomial co-efficients, find coordinates of two end points of lane lines
 
 The results of running on test images are available below:

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...