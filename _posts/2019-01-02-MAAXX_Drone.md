---
layout: post
title: Line Following Drone
---

<img src="/images/drone_10.jpg" alt="main_iamge" class="inline">

This post shows the current state of a project to create a line following drone, with the goal of entering into the [MAAXX](https://maaxx-europe.com/) Competition. *As this project is still in progress, there are many things still to do and things here that will change.*

### System Overview

The project can be split into two main parts. The first part is to find and track the line and the second part is getting the drone to follow the line.

Following a similar method to the [Controlling a Drone with a PS4 Controller](https://jordancormack.github.io/DS4/) post, a Raspberry Pi will be used to send flight commands (RC inputs) to a Betaflight based flight controller. The difference here is that instead of manual control using a PS4 controller, an onboard camera and [OpenCV](https://opencv.org/) will be used to determine what inputs are needed to follow the line.

<img src="/images/drone_overview_1.JPG" alt="overview" class="inline">

### Line Following Method

OpenCV will be used to find and track a line from a camera onboard the drone. Initially a USB webcam was used, but I have now switched to the Pi Camera, mostly to save weight.

Using Python & OpenCV, the video stream from the connected camera is masked based on the desired colour of the line to be followed. Contours on this mask can then be found and the biggest one should be the line. A line of best fit can then be found based on this contour, and the gradient and intercepts with the edges of the frame can be determined. This means we now know where the line is on the screen and the direction it is heading. The below GIF shows a simple script which shows arrows depending on what side of the frame the line is on, and if it is facing left or right.

<img src="/images/drone_early_line.gif" alt="early line tracking" class="inline">

*add more detail and opencv method here with frame captures of each step*

### Pitch/Roll compensation

During flight, when a drone translates left/right/forward/backward it must either pitch or roll the entire body. This is a problem when trying to track a line as the camera view of the line will also shift. To combat this, a gimbal is ususally added to keep the camera straight when the drone is pitching/rolling. Instead of adding a gimbal, my current method takes the pitch and roll angles from the flight controller, and the field of view of the camera, and plots a point directly below the drone. As the drone pitches and rolls, this point will stay fixed below the drone, and allows the code to better understand where the drone is relative to the line on the ground. In theory this removes the need to add a gimbal to the camera.

This theory is shown in the below GIF, where the camera view moves but the blue dot (in the camera view) stays in the same location, directly below the drone.
<img src="/images/test_gif.gif" alt="pitch/roll compensation" class="inline">

*I know there are many problems with the accuracy of this method...but it seems to work well enough for me*

### Control Method

As mentioned in the system overview, this will closely follow the method used in my [Controlling a Drone with a PS4 Controller](https://jordancormack.github.io/DS4/) post. For testing purposes, the drone will default to manual control using the PS4 controller and switch to autonomous flight when a button on the controller is pressed.

One of the main reasons for using a PS4 controller instead of a more standard RC controller for manual flight is that the Betaflight firmware can only accept one input method. This means switching from manual flight using PPM/SBUS etc. to autonomous flight using MSP during flight is not possible, so all flight controll must be done over MSP and switching modes must be done before the input to the flight controller (i.e. on the Pi).
