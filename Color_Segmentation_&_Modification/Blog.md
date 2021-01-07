# Color Segmentation & Modification
>While scrolling through the Fashion section on a shopping website, have you ever thought - "I wish I could change this color, and then this dress would look amazing !!"   
>I have felt the same :D.

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Color_Segmentation_&_Modification/images/Intro.png?raw=true"/>

Working in the Image Processing field gives you the power to make this possible. As we started working on it, we came across this concept of Color Segmentation. The idea was to customize/change the colors present in an image. As we began to research, we came across many amazing articles on color segmentation using Neural Networks & OpenCV (a python library written for the sole purpose of taking up Computer Vision challenges). <br>

There were many cool projects like [*Invisibility Cloak*](https://medium.com/@harshilp/invisibility-cloak-using-opencv-8b07142c83d6) (like the one from the Harry Potter), [*Color Detection*](https://medium.com/programming-fever/color-detection-using-opencv-python-6eec8dcde8c7)(detecting colors in an image), [*Virtual Pen*](https://www.learnopencv.com/creating-a-virtual-pen-and-eraser-with-opencv/)(Used to draw over live webcam), and many others that used color detection/segmentation. Our goal was to do product customization where we can change any color present in a T-Shirt, Furniture, or any other product.<br>

Using Neural Networks might have given us a better accuracy but there were other restraints like training/processing time, and lack of training data.
So, we chose to proceed with OpenCV as it's accuracy can be optimised and is faster as compared to the Neural Networks.<br> 
Here I have explained a few approaches that we tried while working on this project.<br>

---

## Pick the portion containing a certain color.
Have you ever wondered, How does a computer see an image?<br>
It processes the image as a combination of RGB(Red, Green, and Blue) values varying between 0 to 255. Here when all the three values are 0, we see Black color, and when all the three values are 255, we see white color.<br>
While dealing with real-life pictures, we have to deal with shadows and color gradients, which cause varying RGB values.  <br>
Our initial approach was to traverse through the image and set some thresholds to identify a different color. <br>  
**Cons**: Thresholds had to be set manually for each color in each image. As we want the process to be as autonomous as possible, we rejected this idea.<br>

### HSV Color picker: 
HSV(Hue, Saturation & Value) is a cylindrical color model that remaps the RGB primary colors into dimensions that are easier for humans to understand. With the help of this [color space](https://programmingdesignsystems.com/color/color-models-and-color-spaces/index.html), we can identify and mask portions containing a color.  
**Pros**: Good accuracy, Speed.  <br>
**Cons**: HSV values for masking required precision, which only comes with manual work. And hence, we dropped the idea.  <br>

### KNN Algorithm:
KNN (K Nearest Neighbors), as the name suggests it traverses through all the RGB values and plots them on a coordinate plane. You can read more about KNN [here](https://www.analyticsvidhya.com/blog/2018/03/introduction-k-neighbours-algorithm-clustering/).  

**Pros**: 
- Categorizes colors efficiently.
- The only manual input is the number of clusters(or colors in our case).    
  
**Cons**: 
- The processing time for each image is high (about 4 seconds for a 1200x1200 image).
  
    <img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Color_Segmentation_&_Modification/images/Reducedimg05.jpg?raw=true" style="width:300px"/>

Here is how it differentiated between colors which can be further used to make masks. So, our final choice was KNN. KNN comes with the OpenCV module. [Here](https://www.geeksforgeeks.org/implementation-of-knn-using-opencv/), you can find some examples.

---

## Applying a different color on that portion
One might think that this part of the project is easy. Now, as the mask is ready, all we have to do is change the RGB value of the entire masked portion. It is indeed a good solution when we are dealing with images containing solid colors. But, as you can see in our case, we have high RGB variations.<br>
Painting a new color (Changing RGB value directly) would result in loss of texture and light information. So, we'll have to come up with a new way to color the image keeping the textures.<br>

### Grayscale Coloring
What are the textures?
The **Texture** is defined as the physical composition of something or the look and feel of the fabric. An example of texture is the smooth feeling of satin. When the light reacts with the cloth material, it gives rise to textures.<br>
So, this means that we only have to store the light intensity, which can be done with the help of grayscale images.<br>

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Color_Segmentation_&_Modification/images/Grayscale_image.jpg?raw=true" style="width:300px">

As you can see in the image above, all the textures are stored here. Now we can stack the same image thrice and color them R, G, and B(in certain proportions). And then stack them to form a complete image.<br>
<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Color_Segmentation_&_Modification/images/beforeAfterStacked.jpg?raw=true" style="width:400px">    
Here we face another problem, i.e., the intensity of the color applied on the final image doesn't match the actual color that we provided. It is because of the dark areas in the grayscale images. To change the intensity of the color applied, we can increase the intensity of light on the textures and save selective information. Thus, we can add a certain value(I call it a grayscale threshold) to keep the textures with the actual color intensity.<br>

---
## Increasing the customization
Customization in the project can be increased if we can color the portions with the same color differently.<br>
Initially, we made an ROI(Region of Interest) selector. As you can see in the images below, we can select the area and work with it.<br>

### Limitations
While increasing customization, we saw two types of problems:<br>
1. Where the parts to be customized don't overlap with different parts of the same colors.<br>
    <img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Color_Segmentation_&_Modification/images/sport_02.jpg?raw=true" style="width:300px;"/>
It can be solved simply using the ROI selector. All we have to do is select a portion and work with the colors inside it.<br>
   <img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Color_Segmentation_&_Modification/images/ROI.png?raw=true" style="height:300px"><br>

Similarily, we can customize a sport T-shirt.<br>
   <img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Color_Segmentation_&_Modification/images/sport_02_base.jpg?raw=true" style="width:300px;">


2. Here, we saw overlapping(which made the customization a bit difficult).<br>
    <img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Color_Segmentation_&_Modification/images/original_polo.png?raw=true" style="height:300px">
It is quite complex to solve and requires some manual input. Here, we had to make a mask using coordinates to distinguish between different parts of the same color. Once we give it a precise mask around the areas with similar color, Knn does its job.<br>
    <img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Color_Segmentation_&_Modification/images/demo_polo.png?raw=true" style="height:300px">
<br>Here, the results are dependent on the precision of mask.(i.e. the more precise the mask is, the better results you get.)



---


## Conclusion
In this article, we saw some common problems one might face while working with product color customization and their solutions. The goal was to achieve fast results with presentable accuracy. <br>
This field is still under Research & Development, and the complete process may be automated with better accuracy & precision in the future.<br>

---
