---
layout: project
title: Torque Wrench Design
description: Class project
technologies: [ANSYS, Fusion 360, Python]
image: /assets/images/TW-total-deformation.png
---


As part of a class project, I was challenged to design and test a torque wrench that had to adhere to certain requirements. I was first given a base design, and had to iterate from that to get a new design which had to have:

  
  - At least 1.0 mV/V output at the rated torque of 600 in-lbf
  - Safety factor for yield >= 4
  - Safety factor for crack growth >=2 for an assumed crack depth of 0.04 inches
  - Safety factor for fatigue stress >=1.5
  - Material must be a steel ,aluminum, or titanium alloy

1) After writing a python script to determine these values based on the dimensions of the torque wrench, I found that the following dimensions were sufficient, and which can be seen in the following images from Fusion 360 and the diagram of the torque wrench:

  <img src="{{ '/assets/images/TW-dimensions.png' | relative_url }}" alt="Torque Wrench Dimensions" style="max-width:100%;height:auto;border-radius:6px;">

  <img src="{{ '/assets/images/TW-drive-dimensions.png' | relative_url }}" alt="Torque Wrench Drive Dimensions" style="max-width:100%;height:auto;border-radius:6px;">


  - L = 16 inches
  - c = 1 inch
  - h = 0.5 inches
  - b = 0.45 inches
  - Drive is 3/8 inch square and is 0.5 inches tall, with a 0.02 inch radius between the handle and the drive

