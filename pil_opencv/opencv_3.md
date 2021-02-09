# Basic Operation Images

Almost all the operations in this section is mainly related to Numpy rather than OpenCV. A good knowledge of Numpy is required to write better optimized code with OpenCV.

In this section we will talk about:

- Access pixel values and modify them
- Access image properties
- Setting Region of Image (ROI)
- Splitting and Merging images

## Accessing pixel values and modify them

We can access a pixel value by its row and column coordinates. For BGR image, it returns an array of Blue, Green, Red values. For grayscale image, just corresponding intensity is returned.

```python
>>> import cv2
>>> import numpy as np
>>> px = img[100,100]
>>> print px
[157 166 200]

# accessing only blue pixel
>>> blue = img[100,100,0]
>>> print blue
157
```

To modify them :

```python
>>> img[100,100] = [255,255,255]
>>> print img[100,100]
[255 255 255]
```

Above mentioned method is normally used for selecting a region of array, say first 5 rows and last 3 columns like that. For individual pixel access, Numpy array methods, `array.item()` and `array.itemset()` is considered to be better. But it always returns a scalar. So if you want to access all B,G,R values, you need to call `array.item()` separately for all.

```python
# accessing RED value
>>> img.item(10,10,2)
59

# modifying RED value
>>> img.itemset((10,10,2),100)
>>> img.item(10,10,2)
100
```

## Accessing Image Properties

Image properties include number of rows, columns and channels, type of image data, number of pixels etc.

### Shape of Image

Shape of image is accessed by `img.shape`. It returns a tuple of number of rows, columns and channels (if image is color):

```python
>>> print img.shape
(342, 548, 3)
```

### Size of Image

```python
>>> print img.size
562248
```

### Dtype of image

In opencv max. number of errors is due to the wrong data type.
Image datatype is obtained by `img.dtype`:

```python
>>> print img.dtype
uint8
Note
```

## Image ROI

Now,want if we want to select some part of the image but affecting the image,we can just numpy array slizing  for it.

```python
>>> ball = img[280:340, 330:390]
>>> img[273:333, 100:160] = ball
```

## Splitting and Merging Image Channels

The B,G,R channels of an image can be split into their individual planes when needed. Then, the individual channels can be merged back together to form a BGR image again. This can be performed by:

```python
>>> b,g,r = cv2.split(img)
>>> img = cv2.merge((b,g,r))
```

or

```python
>>> b = img[:,:,0]
```

> Note - `cv2.split()` is a costly operation (in terms of time), so only use it if necessary. Numpy indexing is much more efficient and should be used if possible.

## Making Borders for Images (Padding)

If you want to create a border around the image, something like a photo frame, you can use `cv2.copyMakeBorder()` function. But it has more applications for convolution operation, zero padding etc. This function takes following arguments:

- src - input image
- top, bottom, left, right - border width in number of pixels in corresponding directions
- borderType - Flag defining what kind of border to be added. It can be following types:
  - cv2.BORDER_CONSTANT - Adds a constant colored border. The value should be given as next argument.
  - cv2.BORDER_REFLECT - Border will be mirror reflection of the border elements, like this : fedcba|abcdefgh|hgfedcb

- value - Color of border if border type is cv2.BORDER_CONSTANT

There are also some more ,you can read them <a href="https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_core/py_basic_ops/py_basic_ops.html#basic-ops">here</a>.

```python
import cv2
import numpy as np
from matplotlib import pyplot as plt

BLUE = [255,0,0]

img1 = cv2.imread('opencv_logo.png')

replicate = cv2.copyMakeBorder(img1,10,10,10,10,cv2.BORDER_REPLICATE)
reflect = cv2.copyMakeBorder(img1,10,10,10,10,cv2.BORDER_REFLECT)

plt.subplot(231),plt.imshow(img1,'gray'),plt.title('ORIGINAL')
plt.subplot(232),plt.imshow(replicate,'gray'),plt.title('REPLICATE')
plt.show()
```
