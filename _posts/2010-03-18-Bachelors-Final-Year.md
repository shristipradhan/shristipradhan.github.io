---
layout: post
title:  "FPGA Based Acoustic Source Localization"
date:   2010-03-18
excerpt: "Localization of sound source using FPGA, microphones and stepper motor."
tag: false 
project: true
comments: false
---

Acoustic localization is the ability to recognize and determine a sound source's location and draws significant interest for indoor applications.  I worked in a team of four for my Bachelor's final year project. We presented single FPGA implementation of a real time sound source localization system using microphones and stepper motor.

Estimation of direction of arrival of sound can be done effectively by employing multiple, spatially distributed microphones. The implementation was based on generalized cross correlation technique which is based on the time difference of arrival estimation. The relative time delay of the sound signals through microphones can be used to determine the location of sound source. Various other digital signal processing algorithms were also applied.

We built a system with following capabilities:

Capture sound signals with amplification using microphones.

Locate the position of the sound source (implemented on a single FPGA).

Rotate a stepper motor with camera mounted on it pointing to the direction of the sound source.

[Presentation here.](https://www.slideshare.net/shristipradhan1/fpga-based-acoustic-source-localization)
