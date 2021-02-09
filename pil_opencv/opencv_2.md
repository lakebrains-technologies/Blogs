# Drawing Functions in Opencv-python

Here, we will talk about some functions used in opencv like cv2.lines(), cv2.rectangle(), cv2.circle(), etc.

So, let's get started..

## Drawing a line in Opencv

To draw a line, you need to pass starting and ending coordinates of line. We will create a black image and draw a blue line on it from top-left to bottom-right corners.

```python
import numpy as np
import cv2

# Create a black image
img = np.zeros((512,512,3), np.uint8)

# Draw a diagonal blue line with thickness of 5 px
img = cv2.line(img,(0,0),(511,511),(255,0,0),5)
```

## Drawing rectangle in Opencv

To draw a rectangle, you need top-left corner and bottom-right corner of rectangle. This time we will draw a green rectangle at the top-right corner of image.

```python
import numpy as np
import cv2

# Create a black image
img = np.zeros((512,512,3), np.uint8)

# Draws a rectangle with thickness of 3 px given top-leftmost point and bottom-right point of a given color
img = cv2.rectangle(img,(384,0),(510,128),(0,255,0),3)
```

## Drawing a circle in Opencv

To draw a circle, you need its center coordinates and radius. We will draw a circle inside the rectangle drawn above.

```python
import numpy as np
import cv2

# Create a black image
img = np.zeros((512,512,3), np.uint8)

#Drawing the circle here
img = cv2.circle(img,(447,63), 63, (0,0,255), -1)
```

## Drawing a ellipse in Opencv

To make an ellipse,we need to pass several arguements.One arguement is center location(x,y), next is the length of major and minor axis (a,b),others. You can visit <a href="https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_gui/py_drawing_functions/py_drawing_functions.html">here</a> to know in detail.

```python
import numpy as np
import cv2

# Create a black image
img = np.zeros((512,512,3), np.uint8)

#Drawing the ellipse
img = cv2.ellipse(img,(256,256),(100,50),0,0,180,255,-1)
```

## Drawing polygon in Opencv

To draw a polygon, first you need coordinates of vertices. Make those points into an array of shape `ROWSx1x2` where ROWS are number of vertices and it should be of type `int32`. Here we draw a small polygon of with four vertices in yellow color.

```python
import numpy as np
import cv2

# Create a black image
img = np.zeros((512,512,3), np.uint8)

pts = np.array([[10,5],[20,30],[70,20],[50,10]], np.int32)
pts = pts.reshape((-1,1,2))
img = cv2.polylines(img,[pts],True,(0,255,255))
```

And, finally we have here our one and only text too..

## Adding Text to Images

To put texts in images, you need specify following things.

- Text data that you want to write
  
- Position coordinates of where you want put it (i.e. bottom-left corner where data starts).

- Font type (Check cv2.putText() docs for supported fonts)
Font Scale (specifies the size of font)

- regular things like color, thickness, lineType etc. For better look, lineType = cv2.LINE_AA is recommended.
  
```python
import numpy as np
import cv2

# Create a black image
img = np.zeros((512,512,3), np.uint8)

font = cv2.FONT_HERSHEY_SIMPLEX
cv2.putText(img,'OpenCV',(10,500), font, 4,(255,255,255),2,cv2.LINE_AA)
```
