Exp.No : 08 
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
&emsp;
Date : 19.04.2023 
<br>
# Edge-Linking-using-Hough-Transform
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
- **Step 1:** Import all the necessary modules for the program.
- **Step 2:** Load a image using imread() from cv2 module.
- **Step 3:** Convert the image to grayscale.
- **Step 4:** Using Canny operator from cv2,detect the edges of the image.
- **Step 5:** Using the HoughLinesP(),detect line co-ordinates for every points in the images.
- **Step 6:** Using For loop,draw the lines on the found co-ordinates.
- **Step 7:** Display the image.

## Program:
> program by: Kaushika <br> 
> reg no: 212221230048

**Read image and convert it to grayscale image**
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# load the image
in_img=cv2.imread('hq.PNG')
in_img.shape
in_img= cv2.resize(in_img, (510,550))
```

**Find the edges in the image using canny detector and display**
```python
in_img= cv2.resize(in_img, (510,550))
# convert to gray scale
gray_img=cv2.cvtColor(in_img,cv2.COLOR_BGR2GRAY)
noiseless_img = cv2.GaussianBlur(gray_img,(1,1),0)


cv2.imshow('original image',in_img)
cv2.imshow('gray image',gray_img)
cv2.imshow('blurred image',noiseless_img)
cv2.waitKey(0)
cv2.destroyAllWindows()

edges = cv2.Canny(noiseless_img, 50, 150)

cv2.imshow('blurred image',noiseless_img)
cv2.imshow('canny edges image',edges)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


**Detect points that form a line using HoughLinesP()**
```python
lines=cv2.HoughLinesP(edges,1,np.pi/180,threshold=80,
                      minLineLength=50,maxLineGap=50)
```

**Draw lines on the image**
```python
for line in lines:
    x1,y1,x2,y2=line[0]
    cv2.line(in_img,(x1,y1),(x2,y2),(0,0,205),2)
```
**Display the result**
```python
plt.imshow(in_img)
plt.title('HOUGH')
plt.axis('off')
```
## Output

**Input image and grayscale image**

<img src="https://github.com/Kaushika-Anandh/Edge-Linking-using-Hough-Transform/blob/main/1.PNG" width="800" height="200">


**Canny Edge detector output**

<img src="https://github.com/Kaushika-Anandh/Edge-Linking-using-Hough-Transform/blob/main/2.PNG" width="450" height="200">

**Display the result of Hough transform**

<img src="https://github.com/Kaushika-Anandh/Edge-Linking-using-Hough-Transform/blob/main/3.png" width="380" height="410">

## Result:
Thus the program is written with python and OpenCV to detect lines using Hough transform. 
