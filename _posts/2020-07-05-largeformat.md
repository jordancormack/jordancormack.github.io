---
layout: post
title: Pseudo Large Format Digital Camera
image: /images/large_format/Assembly1b.jpg
---

### this post is currently in the process of being written - come back soon!

Large format cameras are ones which are designed to photograph a much larger image than 'standard' cameras. The majoprity of large format cameras are similar to that shown below, which takes a 4x5 (inch) photo using film. The main reason to use a large format camera is to get a higher resolution than standard sized formats. As high resolution digital photography has become more popular, large format film cameras have fallen in popularity.

<img src="/images/large_format/wista.jpg" alt="overview" class="inline">

Below is a comparison of a large format camera, compared to the sensor size of an iPhone, an APS-C sensor which is a common size for most DSLRs, and a full-frame sensor which is used for professional cameras and is equivalent to standard 35mm photography film in size. It can be seen that all of these other film/sensor sizes are dwarfed by that of large format!

<img src="/images/large_format/sensor_sizes.jpg" alt="overview" class="inline">

Old large format lenses can be easily found on sites like eBay for relatively little money, and although using them on a standard digital camera is possible, only the centre of the frame is captured. This is because they are designed for a much larger film/sensor size. From the illustration below, it can be seen that when a large format lens is mounted in front of a standard sized sensor, it can only see a small part of the full image. This reduction in view is commonly known as the 'crop factor'.

<img src="/images/large_format/crop.jpg" alt="overview" class="inline">

In order to produce an image which covers the entire 4x5 frame, instead of rigidly mounting the lens to the camera, a custom frame was been created to translate the camera around the 2D plane of the sensor. Individual images can then be captured and stitched together using a PC to create a single high-resolution image showing the full 4x5 frame projected by the large format lens.

<img src="/images/large_format/pano_gif_2_trim.gif" alt="overview" class="inline">

To move the camera around on a fixed plane, a similar motion mechanism to a 3D printer was used. The frame is constructed using 2020 aluminium extrusion, with the camera mounted to bearings and it is pulled horizontally across smooth rods using a belt connected to a stepper motor. This horizontal axis is mounted at each end to a threaded rod, which raises and lowers the camera using two more stepper motors. The lens is mounted to a rail which allows it to slide backwards and forwards in order to focus. Rigid board is mounted to the back and sides of the frame to block excess light. When photos are taken, the top and front are also covered - aside from a small opening for the lens. The motion system is controlled using a 3D printer control board, with a custom program written using the Arduino IDE.

<img src="/images/large_format/Assembly1b.jpg" alt="overview" class="inline">

Below is a single frame taken with the camera. As expected, the image is quite zoomed in, as it is only seeing a small frame from the middle of what the full lens is projecting.

<img src="/images/large_format/single_frame.jpg" alt="overview" class="inline">

A larger image was then created using a series of individual images, taken by moving the camera around slightly. The images were merged in Photoshop. It can be seen that there are slight differences between individual images, making it easy to spot where one stops and the next one starts.

<img src="/images/large_format/position_only_res.jpg" alt="overview" class="inline">

Photoshop has an option to blend the images and correct for vignetting, which does a good job at eliminating the visible image edges.

<img src="/images/large_format/blended_res.jpg" alt="overview" class="inline">
