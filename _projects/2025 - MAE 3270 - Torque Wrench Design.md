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

**1. Images and dimensions**:

  After writing a python script to determine these values based on the dimensions of the torque wrench, I found that the following dimensions were sufficient, and which can be seen in the following images from Fusion 360 and the diagram of the torque wrench:

  <img src="{{ '/assets/images/TW-dimensions.png' | relative_url }}" alt="Torque Wrench Dimensions" style="max-width:100%;height:auto;border-radius:6px;">

  <img src="{{ '/assets/images/TW-drive-dimensions.png' | relative_url }}" alt="Torque Wrench Drive Dimensions" style="max-width:100%;height:auto;border-radius:6px;">

  <img src="{{ '/assets/images/TW-full-length.png' | relative_url }}" alt="Torque Wrench Drive Dimensions" style="max-width:100%;height:auto;border-radius:6px;">

  <img src="{{ '/assets/images/TW-length.png' | relative_url }}" alt="Torque Wrench Drive Dimensions" style="max-width:100%;height:auto;border-radius:6px;">

  <img src="{{ '/assets/images/TW-b-h.png' | relative_url }}" alt="Torque Wrench Drive Dimensions" style="max-width:100%;height:auto;border-radius:6px;">
  - L = 16 inches
  - c = 1 inch
  - h = 0.5 inches
  - b = 0.45 inches
  - Drive is 3/8 inch square and is 0.5 inches tall, with a 0.02 inch radius between the handle and the drive

**2. Material Used**:

  The material I picked for this design was AISI 4140 low alloy steel, oil quenched and tempered at 425℃

- E = 31.3e6 psi
- $\sigma_y = 182 ksi
- Fatigue (10^6 cycles) = 102 ksi
- Kic = 57.3 ksi*sqrt(in)

**3. Boundary Conditions and Loads**:

  Below is an image showing the clamped boundary condition on the top 0.4 inches of the drive, and the 37.5 lbf on the end of the handle, generating a moment of 600 in*lbf

  <img src="{{ '/assets/images/TW-load-boundary.png' | relative_url }}" alt="Torque Wrench Drive Dimensions" style="max-width:100%;height:auto;border-radius:6px;">

**4. Normal Strain Contours From FEM**:

  The normal elastic strain of the torque wrench can be seen below. The maximum and minimum values are 0.0018153 and -0.0016909, respectively. These strains are located on the drive, and are due to stress concentrations. Along the handle, the strain varies with a smaller range

  <img src="{{ '/assets/images/TW-normal-elastic-strain.png' | relative_url }}" alt="Torque Wrench Drive Dimensions" style="max-width:100%;height:auto;border-radius:6px;">

**5. Contour Plot of Maximum Principal Stress From FEM**:

  The maximum principal stress of the torque wrench can be seen below. The maximum and minimum values are 163 ksi and -868.2 psi, respectively. The maximum is due to stress concentrations between the handle and the drive, as the maximum along the handle is only around 35 ksi.

  <img src="{{ '/assets/images/TW-max-principal-stress.png' | relative_url }}" alt="Torque Wrench Drive Dimensions" style="max-width:100%;height:auto;border-radius:6px;">

**6. Results From FEM Calculation**:

  Shown below is the results of the normal stress, load point deflection, and strain at the strain gauge simulations in ANSYS. 

  - Normal Stress:
    <img src="{{ '/assets/images/TW-normal-stress.png' | relative_url }}" alt="Torque Wrench Drive Dimensions" style="max-width:100%;height:auto;border-radius:6px;">
    
    The maximum normal stress in the torque wrench was 50.429 ksi, located at the connection between the handle and drive. The rest of the handle had a normal stress of around 5 ksi


  - Load Point Deflection:
    <img src="{{ '/assets/images/TW-total-deformation.png' | relative_url }}" alt="Torque Wrench Drive Dimensions" style="max-width:100%;height:auto;border-radius:6px;">
 
    The maximum deflection of the torque wrench was 0.47742 inches, located at the end of the handle. This is expected, with the total deformation decreasing as the point gets closer to the drive


  - Strain at Strain Gauge:
    <img src="{{ '/assets/images/TW-strain-probe.png' | relative_url }}" alt="Torque Wrench Drive Dimensions" style="max-width:100%;height:auto;border-radius:6px;">

    The strain at the strain gauge, located 1 inch from the middle of the drive, is 1.0643e-3, or 1064 microstrain

**7. Torque Wrench Sensitivity**:

  Using the 1064 microstrain from the FEM analysis, the sensitivity k can be calculated by divinding the output by the strain at the gauge. Using an output of 0.38mV/V from the base design, the sensitivity k is equal to 2,800


**8. Strain gauge selected**:

  I used a half bridge strain gauge for this analysis, just like the one used in the base design. 