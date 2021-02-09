# Getting Started with OpenCV in Python

OpenCV is a cross-platform library using which we can develop real-time computer vision applications. It mainly focuses on image processing, video capture and analysis including features like face detection and object detection.

Here,in our case for now we will discussing opencv with python.

## Requirements

- Numpy
- Matplotlib
- opencv

Above modules can be imported in python via command prompt in windows like this -

``pip install numpy``

``pip install matplotlib``

``pip install opencv-python``

That's it for installation ! Now, time for some coding..

## Creating first opencv program

```python
import numpy as np
import cv2

# Load an color image in grayscale
img = cv2.imread('image_name.jpg',0)

#Displaying an image with a title - 'image'
cv2.imshow('image',img)

#Waiting until any key is pressed
cv2.waitKey(0)

#If any key is pressed,then it closes that window
cv2.destroyAllWindows()
```
Firstly ,we imported numpy image is in form of an array and cv2 for using opencv in python.

We simply read the image in the grayscale mode which means it's color value lies between 0 to 255 not in different color channels for now.

## Saving a Image using opencv

```python
import numpy as np
import cv2

# Load an color image in grayscale
img = cv2.imread('image_name.jpg',0)

cv2.imshow('image',img)
k = cv2.waitKey(0)

if key == 27:       # Waiting for the escape key to be pressed
    cv2.destroyAllWindows()

elif k == ord("s"):     #Wait until s is pressed,then save and exit

    #This helps in saving the images
    cv2.imwrite("image_name_gray.png",img)
```

Here, what we did is that we read an image and showed it, then we waited till, that when we press ESC it quits,and if we press 's' key it saves the grayscale image and then quits.

## Capture video from camera

```python
import numpy as np
import cv2

cap = cv2.VideoCapture(0)

while(True):
    # Capture frame-by-frame
    ret, frame = cap.read()

    # Our operations on the frame come here
    #cv2.cvtColor() function of cv2
    #cv2.COLOR_BGR2GRAY converts the image to grayscale image
    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)

    # Display the resulting frame
    cv2.imshow('frame',gray)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

# When everything done, release the capture
cap.release()
cv2.destroyAllWindows()
```

In this case,we already know that an video is just an series of images so we go through each one of them and converted them to the grayscale image and then waiting until 'q' is pressed, so that we can quit.

## Playing a video from a file

It is same as capturing from Camera, just change camera index with video file name. Also while displaying the frame, use appropriate time for `cv2.waitKey()`. If it is too less, video will be very fast and if it is too high, video will be slow (Well, that is how you can display videos in slow motion). 25 milliseconds will be OK in normal cases.

```python
import numpy as np
import cv2

#Reading Video File
cap = cv2.VideoCapture('vtest.avi')

#Looping through it's frames
while(cap.isOpened()):
    ret, frame = cap.read()

    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)

    cv2.imshow('frame',gray)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
```

You can go to official page to know more which is <a href="https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_gui/py_table_of_contents_gui/py_table_of_contents_gui.html">here</a>

This is it for basic of opencv in python, let's jump onto more on further time.
