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

Python is used on the Raspberry Pi to plan a route for the motion system to take. The 

<img src="/images/gigapi/crop_1.png" alt="overview" class="inline">
<img src="/images/gigapi/crop_2.png" alt="overview" class="inline">
<img src="/images/gigapi/overal_1.png" alt="overview" class="inline">
<img src="/images/gigapi/overlap_3.png" alt="overview" class="inline">

<img src="/images/gigapi/full_image_2_pi.jpg" alt="overview" class="inline">
<img src="/images/gigapi/full_image_gray.jpg" alt="overview" class="inline">

<img src="/images/gigapi/test4_stitch_4MP.jpg" alt="overview" class="inline">
<img src="/images/gigapi/test4_stitch_crop.jpg" alt="overview" class="inline">

<iframe allowfullscreen="true" src="https://www.easyzoom.com/embed/99bca385b89c45bc9f45732602ef78cb" width="400" height="300"></iframe>

*This post is in the process of being written*
