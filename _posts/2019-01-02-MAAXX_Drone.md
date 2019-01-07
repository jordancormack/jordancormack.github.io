---
layout: post
title: Line Following Drone
---

This post shows the current state of a project to create a line following drone, with the goal of entering into the [MAAXX](https://maaxx-europe.com/) Competition. *As this project is still in progress, there are many things still to do and things here that will change.*

### System Overview

The project can be split into two main parts. The first part is to find and track the line and the second part is getting the drone to follow the line.

Following a similar method to the [Controlling a Drone with a PS4 Controller](https://jordancormack.github.io/DS4/) post, a Raspberry Pi will be used to send flight commands (RC inputs) to a Betaflight based flight controller. The difference here is that instead of manual control using a PS4 controller, an onboard camera and [OpenCV](https://opencv.org/) will be used to determine what inputs are needed to follow the line.

### Line Following Method

OpenCV will be used to find and track a line from a camera onboard the drone. Initially a USB webcam was used, but I have now switched to the Pi Camera, mostly to save weight.

*add opencv method here with frame captures of each step*

### Pitch/Roll compensation

During flight, when a drone translates left/right/forward/backward it must either pitch or roll the entire body. This is a problem when trying to track a line as the camera view of the line will also shift. To combat this, a gimbal is ususally added to keep the camera straight when the drone is pitching/rolling. Instead of adding a gimbal, my current method takes the pitch and roll angles from the flight controller, and the field of view of the camera, and plots a point directly below the drone. As the drone pitches and rolls, this point will stay fixed below the drone, and allows the code to better understand where the drone is relative to the line on the ground. In theory this removes the need to add a gimbal to the camera.

*add a GIF and a figure explaining this better*

### Control Method

As mentioned in the system overview, this will closely follow the method used in my [Controlling a Drone with a PS4 Controller](https://jordancormack.github.io/DS4/) post. For testing purposes, the drone will default to manual control using the PS4 controller and switch to autonomous flight when a button on the controller is pressed.

One of the main reasons for using a PS4 controller instead of a more standard RC controller for manual flight is that the Betaflight firmware can only accept one input method. This means switching from manual flight using PPM/SBUS etc. to autonomous flight using MSP during flight is not possible, so all flight controll must be done over MSP and switching modes must be done before the input to the flight controller (i.e. on the Pi).
