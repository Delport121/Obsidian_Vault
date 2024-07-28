[Geeksforgeeks](https://www.geeksforgeeks.org/opencv-python-tutorial/?ref=lbp)
# Getting started
## Colour spaces
*Color spaces* are a way to represent the color channels present in the image that gives the image that particular hue.
- OpenCV’s default color space is RGB. However, it actually stores color in the BGR format.
The are three types of colour spaces:
- RGB 
- HSV 
- CMYK
## Arithmetic operations
### Addition and Subtraction
By adding two images together, you can create a combined image which looks pretty cool. Similarly, you can also subtract intensity values from one image using another image.
### Bitwise operations on binary images
- Bitwise operations should be applied on images with the same dimensions.
It has all the usual operations such as:
- AND
- OR
- XOR
- NOT
# Image processing
- Resizing images
- cv2.erode() method
- Image blurring
	- *Gaussian Blurring:* Gaussian blur is the result of blurring an image by a Gaussian function. It is a widely used effect in graphics software, typically to reduce image noise and reduce detail. It is also used as a preprocessing stage before applying our machine learning or deep learning models. E.g. of a Gaussian kernel(3×3)
	- *Median Blur:* The Median Filter is a non-linear digital filtering technique, often used to remove noise from an image or signal. Median filtering is very widely used in digital image processing because, under certain conditions, it preserves edges while removing noise. It is one of the best algorithms to remove Salt and pepper noise.
	- *Bilateral Blur:* A bilateral filter is a non-linear, edge-preserving, and noise-reducing smoothing filter for images. It replaces the intensity of each pixel with a weighted average of intensity values from nearby pixels. This weight can be based on a Gaussian distribution. Thus, sharp edges are preserved while discarding the weak ones

- Particle filter
- Adjustable bracket