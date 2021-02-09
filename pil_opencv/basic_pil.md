# Use Pillow to paste an image over another image

Firstly, we need know what is pillow ! Pillow is basically a fork of the library called PIL which was an Image Processing library whose support got discontinued but Pillow's still remain. Pil can only used in Python 2x, but now's the time for Pillow in Python 3x.

## Installing Pillow

```cmd
pip install pillow
```

Now time to use it!!

## Reading images and saving them

```python
from PIL import Image

img = Image.open("dog.jpg")
img.save("dog_2_png.png")
```

Here we are simply importing our requirements,reading an image `dog.jpg`,and then saving that image in another format.
Here's a catch if want to convert a jpg,etc except formats to png it's possible but for it's vice-versa it's not due to difference in the number of color channels.

## Making image thumbnails

Thumbnails are quite useful when we want to store large amount of images when there is a limited storage. In python, we can do this like this :

```python
from PIL import Image

size = (300,300)

#Reading the image
img=Image.open("dog.jpg")

#Changing the size to 300 x 300
img.thumbnail(size)

#Saving the resized img
img.save("resized_img.jpg")
```

## Pasting an image over another image

Sometimes,we want to put an image over another image, we can also do this in python using pillow like this

```python
from PIL import Image

front_img = Image.open("dog.jpg")
back_img = Image.open("background.png")

back_img.paste(front_img)
back_img.save("pasted_img.png",quality =90)
```

Here,the image is pasted at (0,0) pixel as a default
Want if we want image at a given place?
It will be like this:

```python
from PIL import Image

place=(120,50)
front_img = Image.open("dog.jpg")
back_img = Image.open("background.png")

back_img.paste(front_img,place)
back_img.save("pasted_img.png",quality =90)
```

But,remember that the background image should be larger or eual to the image being pasted

## Pastimg an Image over another image but with some area

Pillow also allows you to cut the image with respect with other images while pasting. This is how it happens :

```python
from PIL import Image, ImageDraw, ImageFilter

front_img = Image.open("dog.jpg")
back_img = Image.open("background.jpg")

#Creating a blank image to edit
mask_img = Image.new("L",front_img.size,0)

# Make blank image drawable in simple words
draw = ImageDraw.Draw(mask_img)

#Created an ellipse with given values and filled it with white color
draw.ellipse((140,50,260,170),fill = 255)
mask_img.save("mask_img.jpg")

#Copying the background image as it gets overwritten during the process
back_img_copy = back_img.copy()

#It will paste front_img at 100,100 with respect to the mask_img
back_img_copy.paste(front_img,(100,100),mak_img)

#Saving the final image
back_img_copy.save("pasted.jpg")
```

## Pasting image with filters

Pillow also allows the use of filters while pasting an image over another like having a smooth transition between them,etc.
An exmple of this is :

```python
from PIL import Image, ImageDraw, ImageFilter

front_img = Image.open("dog.jpg")
back_img = Image.open("background.jpg")

#Creating a blank image to edit
mask_img = Image.new("L",front_img.size,0)

# Make blank image drawable in simple words
draw = ImageDraw.Draw(mask_img)

#Created an ellipse with given values and filled it with white color
draw.ellipse((140,50,260,170),fill = 255)

#Blurring the image using gaussain blur 
mask_img_blur = mask_img.filter(ImageFilter.GaussainBlur(10))
mask_img.save("mask_img_blur.jpg")

#Copying the background image as it gets overwritten during the process
back_img_copy = back_img.copy()

#It will paste front_img at 100,100 with respect to the mask_img
back_img_copy.paste(front_img,(100,100),mak_img_blur)

#Saving the final image
back_img_copy.save("final_pasted.jpg")
```

## Making certain regions transparent in a image

Sometimes,when we want to make certain part in a image we can easily do that with pillow
Here is an example of how to do it when the background of the image is same ,in this -

```python
from PIL import Image

def get_image(img_on,img_put):
    
    img1 = Image.open(img_on)
    img2 = Image.open(img_put)
    #img2.show()

    #Converting the image to 4-color channeled
    img2 = img2.convert("RGBA")
    datas = img2.getdata()

    newData = []
    w,h = img2.size
    coords1 = [0,0]
    coords2 = [w,0]
    coords3 = [0,h]
    coords4 = [w,h]

    #Getting the RGBA values in the corners
    pixel_value1 = datas[coords1[0]]
    pixel_value2 = datas[coords2[0]]
    pixel_value3 = datas[coords3[0]]
    pixel_value4 = datas[coords4[0]]

    #Checking if the cornor pixel color values are same or not
    if (pixel_value1 == pixel_value2) and (pixel_value3 == pixel_value4) and (pixel_value2 == pixel_value3):
        back_gf = list(pixel_value1)
        print(back_gf)
    
        for item in datas:
            if (item[0] == back_gf[0]) and (item[1] == back_gf[1]) and (item[2] == back_gf[2]):        
                newData.append((255, 255, 255, 0))
            else:
                newData.append(item)
        
        img2.putdata(newData)

        #Ignoring RGB values where alpha==0
        img1.paste(img2,(1,1),img2)
        img1.show()
    else:
        print("Not,possible! Value of background cornor color pixels doesn't match !!")

img_put = "front_image.png"
img_on ="background_image.png"
get_image(img_on,img_put)
```

Well that's it for this blog, catch you up next XD !! Don't forgot to check for the offical documentation know more.
