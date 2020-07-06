---
layout: post
title: Pseudo Large Format Digital Camera
image: /images/large_format/Assembly1b.jpg
---

Large format cameras are ones which are designed to photograph a much larger image than 'standard' cameras. The majority of large format cameras are similar to that shown below, which takes a 4x5 (inch) photo using film. The main reason to use a large format camera is to get a higher resolution than standard sized formats. As high resolution digital photography has become more popular, large format film cameras have fallen in popularity.

<img src="/images/large_format/wista.jpg" alt="overview" class="inline">

Below is a comparison of a large format camera frame, compared to the sensor size of an iPhone, an APS-C sensor which is a common size for most DSLRs, and a full-frame sensor which is used for professional cameras and is equivalent to standard 35mm photography film in size. It can be seen that all of these other film/sensor sizes are dwarfed by that of large format!

<img src="/images/large_format/sensor_sizes.jpg" alt="overview" class="inline">

Old large format lenses can be easily found on sites like eBay for relatively little money, and although using them on a standard digital camera is possible, only the centre of the frame is captured. This is because they are designed for a much larger film/sensor size. From the illustration below, it can be seen that when a large format lens is mounted in front of a standard sized sensor, it can only see a small part of the full image. This reduction in view is commonly known as the 'crop factor'.

<img src="/images/large_format/crop.jpg" alt="overview" class="inline">

In order to produce an image which covers the entire 4x5 frame, instead of rigidly mounting the lens to the camera, the camera can be translated around the 2D plane of the sensor. Individual images can then be captured and stitched together using a PC to create a single high-resolution image showing the full 4x5 frame projected by the large format lens.

<img src="/images/large_format/pano_gif_2_trim.gif" alt="overview" class="inline">

To move the camera around on a fixed plane, a similar motion mechanism to a 3D printer was used. The frame is constructed using 2020 aluminium extrusion, with the camera mounted to bearings which run on smooth rods. The camera is pulled left and right using a belt connected to a stepper motor. This horizontal axis is mounted at each end to a threaded rod, which raises and lowers the camera using two more stepper motors. The lens is mounted to a rail which allows it to slide backwards and forwards in order to focus. Rigid board is mounted to the back and sides of the frame to block excess light. The motion system is controlled using a 3D printer control board, with a custom program written using the Arduino IDE.

<img src="/images/large_format/Assembly1b.jpg" alt="overview" class="inline">

Below are a few images of the initial camera setup. The rigid back and side panels can be seen, along with a flexible black front piece. Another black piece is placed on top when the camera is in use to block more excess light from entering. In an ideal world the camera rig would be completely light sealed aside from the lens - this will be done once the camera rig is fully functional. A Raspberry Pi is mounted to the back board which controls the camera and sends commands to the 3D printer control board below it.

<img src="/images/large_format/camera_iso.jpg" alt="overview" class="inline">
<img src="/images/large_format/camera_top.jpg" alt="overview" class="inline">
<img src="/images/large_format/camera_back.jpg" alt="overview" class="inline">

As stepper motors do not have any built-in position sensing, two switches were added which allows the system to find a 'home' position as a point of reference. The stepper motors are then calibrated and so can move from this home position to wherever the program commands.

<img src="/images/large_format/camera_home.jpg" alt="overview" class="inline">

### Test 1: Using a Canon 6D

Below is a single frame taken with the camera. As expected, the image is quite zoomed in, as it is only seeing a small frame from the middle of what the full lens is projecting.

<img src="/images/large_format/single_frame.jpg" alt="overview" class="inline">

A larger image was then created using a series of individual images, taken by moving the camera around slightly. The images were merged in Photoshop. It can be seen that there are slight differences between individual images, making it easy to spot where one stops and the next one starts.

<img src="/images/large_format/position_only_res.jpg" alt="overview" class="inline">

Photoshop has an option to blend the images and correct for vignetting, which does a good job at eliminating the visible individual image edges. The resolution of this image is 16507x6906 (approximately 114 megapixels).

<img src="/images/large_format/blended_res.jpg" alt="overview" class="inline">

The above test images are only taken from a small section of the overal large format lens projection (see below for an approximation). More will be posted soon with an even larger field of view and resolution.

<img src="/images/large_format/inner_frame.jpg" alt="overview" class="inline">

### Test 2: Nikon 1 J2

Although the Canon 6D performed well, further testing will be done using a Nikon 1 J2. Compared to the Canon, this Nikon has a smaller sensor but a higher pixel density. This means that more individual images will need to be taken to produce the same field of view, but the final resolution will be higher. I will also be switching from using Photoshop to merge the images, to using [Microsoft Image Composite Editor](https://www.microsoft.com/en-us/research/product/computational-photography-applications/image-composite-editor/) (MS ICE). Below is the a series of images taken using the Nikon, aligned but pre-stitching. The overall image is visable, but there are some initially strange artifacts to the right of the image. As the camera sensor is recessed into the body of the camera, as it moves to the side, the body begins to obstruct the sensor's view of the lens. This causes part of that individual image frame to contain a black bar on one side.

<img src="/images/large_format/pano_nikon_1.jpg" alt="overview" class="inline">

There is also a pink shift to the individual images on the right. This is due to a colour shift in a protective layer on top of the camera sensor when viewed off axis (shown in a GIF below)

<img src="/images/large_format/pink_shift.gif" alt="overview" class="inline">

The stitched image is 34640x9743 pixels, which is equal to 337.5 megapixels. When MS ICE attempts to stitch the images together, it tries to match the brightness of each individual image to those which surround it. In a 'normal' panorama this makes perfect sense, however as some of these images have a dark side due to the body obstructing the sensor, this causes some strange exposure issues for these frames. One way to fix this issue is to take more images which overlap each other. This would ensure that there is always at least one frame which shows the un-obstructed view. MS ICE has also tried to level the exposure across the overal stitched image, which has caused the left hand side to become much darker than the original individual frames.

<img src="/images/large_format/pano_nikon_1_stitch_smaller.jpg" alt="overview" class="inline">

### more to come soon!
