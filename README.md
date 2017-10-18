# **Finding Lane Lines on the Road** 


 Identify lane lines on the road, first in an image, and later in a video stream. 


[//]: # (Image References)
[original]: ./examples/original.png "Original"
[Grayscale]: ./examples/grayscale.png "Grayscale"
[gaussian]: ./examples/gaussian.png "Gaussian"
[Canny]: ./examples/canny.png "Canny"
[masked]: ./examples/masked.png "Masked"
[hough]: ./examples/hough.png "Hough"
[result]: ./examples/result.png "Result"


### Reflection



My pipeline consisted of 5 steps. Inside the "proccess_image(image)":

![alt text][original]

1-  "image" parameter is converted the images to grayscale using grayscale: 

![alt text][Grayscale]

2-  Then, the grayscale image is passed to the gaussian_blur function to smooth the edges:

![alt text][gaussian]


3- Passed the resulting image from "gaussian\_blur" to the "canny" function. The values for the low\_threshold and hight_threshold, 50 and 150, respectively.

![alt text][canny]


4- Using the "region\_of\_interest" function, to mask out the unwanted part of the picture and keep the area that contains the lane lines:

![alt text][masked]


5- Then, I passed the masked image to "hough\_lines" function which finds the lane lines in the image we detected edges in with the Canny function. After many combinations trials, I found (rho = 5, theta = np.pi/180, threshold = 150, min\_line\_len = 50, max\_line\_gap = 120) combination, produce the best result:

![alt text][hough]


6- Lastly, I passed the hough image and the original image to the "weighted_img" function to produce the original image with detected lane lines drawn on it:

![alt text][result]





### Shortcomings:


The helper functions' parameters combination, that are set inside "process\_image", might need to be changed everytime we have an image taken with a different camera position.




### Suggested Improvements to your pipeline

A possible improvement would be to have set of profiles for different camera positions and settings. Each has parameters value combination for the helper functions. Then we can use any profile inside the "process_image" function, depending on the image.


