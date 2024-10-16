# Edge-Linking-using-Hough-Transformm
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:

Import all the necessary modules for the program.
### Step2:

Load a image using imread() from cv2 module.
### Step3:

Convert the image to grayscale.
### Step4:

Using Canny operator from cv2,detect the edges of the image.
### Step5:

Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.Display the image.

## Program:
```
Developed by: Giftson Rajarathinam N
Reg.No: 212222233002

import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('fish.png')  # Replace with your image path

gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

edges = cv2.Canny(gray_image, 50, 150, apertureSize=3)

# Detect lines using the probabilistic Hough transform
lines = cv2.HoughLinesP(edges, rho=1, theta=np.pi/180, threshold=100, minLineLength=50, maxLineGap=10)

# Draw the lines on the original image
output_image = image.copy()

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(output_image, (x1, y1), (x2, y2), (0, 255, 0), 2)

# Displaying results using Matplotlib
plt.figure(figsize=(12, 12))

# Input Image and Grayscale Image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Input Image')
plt.axis('off')

plt.imshow(gray_image, cmap='gray')
plt.title('Grayscale Image')
plt.axis('off')

# Canny Edge Detection Output
plt.imshow(edges, cmap='gray')
plt.title('Canny Edge Detector Output')
plt.axis('off')

# Hough Transform Result
plt.imshow(cv2.cvtColor(output_image, cv2.COLOR_BGR2RGB))
plt.title('Hough Transform - Line Detection')
plt.axis('off')

# Display all results
plt.show()

```
## Output

### Input image and grayscale image:
![Screenshot 2024-10-16 134522](https://github.com/user-attachments/assets/e9708106-432f-472e-83ec-c99ad44de469)

![Screenshot 2024-10-16 134604](https://github.com/user-attachments/assets/71d6eaa8-06a7-4459-85c4-a160fda06800)


### Canny Edge detector output:
![Screenshot 2024-10-16 134639](https://github.com/user-attachments/assets/cd978b91-028f-434f-9f66-a13d79c50a02)


### Display the result of Hough transform:
![Screenshot 2024-10-16 134716](https://github.com/user-attachments/assets/00af9cc6-fa72-40c4-906a-324ca94d3b41)

### Result:
Successfully converted the given image to Canny edge detector and Hough transform method and displayed using python.
