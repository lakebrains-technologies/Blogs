title: Image Overlaying I/I 
date: 10 Jan 20
auther: Yash Mali
description: While different kinds of image filters on different platforms ever wondered how it happens, then you are going to know it works.
img: "https://github.com/lakebrains-technologies/Blogs/blob/master/Color_Segmentation_&_Modification/images/Intro.png?raw=true"
tab_id: vision-processing

# Logo on another image

## Requirements

Modules required:

- numpy
- matplotlib

## Execution

1. Select two images, one foreground and another for background
2. Select a coordinate over background image to paste the image there.
3. After doing this,click the submit button.
4. Wallah, now you can see the new image appeared over the background image

### How it works

1. Finding the main region i.e. region of interest(ROI) using methods in opencv

2. Now after finding that region making sure that ROI is looks similar to how was in the original form

3. Now,making the area other than our ROI kind of transparent, so that it does not image, look kinda bad. In this we have done,it using making the alpha/transparent channel for outside our  ROI and for ROI it definitely has to be not transparent, so making alpha value to 255.

4. Now, all we need to do is make the area where we want the image to be in the background according to us, so what we need to do is simple slicing and replacing their values, simple XD.

5. Now we get our new image using opencv,yeah we have completed  it.

### Let's see how it looks with some examples

Our ``foreground`` image here is our  logo and ``background`` is some random image

<img src="img2.png" alt="Logo" width="200"/> 

<br>

<img src="image_ko.png" alt="Background" width="400" height="200"/> 

After applying above things, it looks like this  

<img src="combined_image.png" alt="Combined Image" width="400" height="300"/>