---
layout: post
title: "Generative Design in Fusion 360: Inital Study"
image: /images/Generative_Design_16.JPG
---

This post looks at my initial testing of Fusion 360's generative design process. Generative design is an iterative design process that uses artificial intelligence to generate the part geometry, based on a series of input parameters, such as the desired material and manufacturing process - this differs to topology optimisation, which essentially just cuts away regions of the part where the stress is low.

These tests will focus on a small 3D printable drone arm, which I initally designed for the [SciRoc autonomous drone competition](https://jordancormack.github.io/SciRoc-2019/). The arm which I previously designed is shown below. On the left there is a mount for the motor and on the right there is a mount to the drone body. A hole was added for the motor cables, which will not be considered for the following generative design study.

<img src="/images/Human_Design_1crop.jpg" alt="" class="inline">

To start the generative design process, only the essential geometry was created in Fusion 360. In this case, just the motor mount, and the body mount. The distance between these mounts was also specified.

<img src="/images/Generative_Design_1crop.jpg" alt="" class="inline">

To ensure that the generateive design process deos not add material in undesired locations, additional solid bodies were created in regions where access is needed - in this case for bolts or nearby components such as the motor and body.

<img src="/images/Generative_Design_5crop.jpg" alt="" class="inline">

Next, the essential geometry is set to 'preserve' shown in green, and the other bodies are set to 'obstacle' in red. The structural loads and constraints can also be added. Here shown by the vertical motor force, and the fixed body mount.

<img src="/images/Generative_Design_22.JPG" alt="" class="inline">

Since generative design in Fusion 360 takes into account the material and manufacturing process, these can also be specified. I have selected PA11 as the material and additive manufacturing and the process. Within the addditive manufacturing settings, a max overhang angle and mininimum wall thickness can also be set. The generative design objective was set to minimise stress, with the default safety factor left at 2.00 (a maximise stiffness objective is also available). A previewer runs the first few design iterations, to allow you to check if the study has any obvious errors. It can be seen that the initial geometry is not too dissimilar to my 'human designed' arm.

<img src="/images/Generative_Design_13crop.jpg" alt="" class="inline">

The generative design process can then be started. Instead of asking the user to specify the print orientation in the additive manufacturing setting, the generative design process gives three separate 'outcomes' - one for each of the XYZ axis. This means that the geometry will be designed in a way to *hopefully* produce a part which is not only optimised for the load, but also for manufacture.

<img src="/images/Generative_Design_23.jpg" alt="" class="inline">
