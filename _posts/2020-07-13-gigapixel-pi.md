---
layout: post
title: Gigapixel Photography with the Raspberry Pi
image: /images/gigapi/thumb.jpg
---

In early 2020 the Raspberry Pi Foundation released the (Pi HQ Camera)[https://www.raspberrypi.org/blog/new-product-raspberry-pi-high-quality-camera-on-sale-now-at-50/]. It features a sensor which is bigger and higher resolution than previous Pi cameras, and it is designed for use with C or CS-mount lenses (which are commonly used in things like CCTV cameras). This is great, but what if you want to take even higher resolution images with your Raspberry Pi? 

I created a motion system which moves the Raspberry Pi HQ camera around a 2D plane, behind a fixed position large format lens. As this lens projects an image many times larger than the sensor of the Pi HQ camera, as the camera is moved around behind it, images can be taken at muliple locations which can later be stitched into a single high resolution image. The motion system is an updated version of the one shown in my previous blog post ((Pseudo Large Format Digital Camera)[https://jordancormack.github.io/largeformat/]).

<img src="/images/gigapi/CAD_1.jpg" alt="overview" class="inline">
<img src="/images/gigapi/outside_1.jpg" alt="overview" class="inline">
<img src="/images/gigapi/inside_1.jpg" alt="overview" class="inline">
<img src="/images/gigapi/rear_1.jpg" alt="overview" class="inline">

The stepper motors are conencted to the old 3D printer control board, and a basic program was created using the Arduino IDE which takes takes commands from the Raspberry Pi. These commands tell the control board what direction to turn the stepper motors, and how many steps to move by. There is also a 'home' command which runs at the start of the program to position the camera in a known location.

<img src="/images/gigapi/electronics.jpg" alt="overview" class="inline">

Python is used on the Raspberry Pi to plan a route for the motion system to take. The user inputs the number of desired rows and columns which the final image will be made up of, and the starting position and path is generated. This path is centered behind the lens, in the middle of the known limits of the motion system . The path and individual image locations are then plotted. This path planner also has an input for image overlap - which is useful both for blending the images later, or producing a coarse test path.

<img src="/images/gigapi/overal_1.png" alt="overview" class="inline">
<img src="/images/gigapi/crop_1.png" alt="overview" class="inline">
<img src="/images/gigapi/crop_2.png" alt="overview" class="inline">
<img src="/images/gigapi/overlap_3.png" alt="overview" class="inline">

Once the path is confirmed, the Raspberry Pi sends each movement command to the motor control board, stopping to take an image at each pre-generated location. Once all of the images are taken, they can be processed and aligned to form a complete single image using NumPy and OpenCV. Although this image stitching can be done on the Pi 4, the overall resolution is limited by the availiable RAM. This means that images of *only* around 500 megapixels can be created. One of the images stitched using this NumPy/OpenCV method on the Pi is shown below. Although the lens aperture and camera ISO, shutter speed and white balance are supposedly fixed, there are clear inconsistencies between the individual images. Some of these can be fixed by converting the image to greyscale, but the individual images are still noticable. Using overlapping images, proper image stitching is (possible with OpenCV)[https://www.pyimagesearch.com/2018/12/17/image-stitching-with-opencv-and-python/] but I have not yet tried this approach.

<img src="/images/gigapi/full_image_2_pi.jpg" alt="overview" class="inline">
<img src="/images/gigapi/full_image_gray.jpg" alt="overview" class="inline">

I have done a test using Microsoft Image Composite Editor, which does a good job at blending the image together (some faint lines and mis-matched edges are visable), and can stitch images at over 1,000 megapixels. This equates to a 10x10 grid of images using the Pi HQ camera, with an overlap of around 10%. A reduced resolution image is shown below, along with a cropped region.

<img src="/images/gigapi/test4_stitch_4MP.jpg" alt="overview" class="inline">
<img src="/images/gigapi/test4_stitch_crop.jpg" alt="overview" class="inline">

See below for a full-resolution view.

<iframe allowfullscreen="true" src="https://www.easyzoom.com/embed/99bca385b89c45bc9f45732602ef78cb" width="400" height="300"></iframe>

*This post is in the process of being written*
