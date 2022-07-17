---
title: "Mars Rover"
date: 2021-06-13T12:44:47.000Z
extra:
  link: https://github.com/neeldug/EEE2Rover
  image: /media/mars-rover.svg
description: A group project aiming to replicate basic functionality of a Mars rover
taxonomies:
  tags:
    - SystemVerilog
---
### MIPS CPU

My contribution to the Mars rover was the Vision subsystem:

* RGB-HSV colour conversion for easier ball-detection mechanism
* Run-length based filtering to eliminate noise
* Attempted use of Sobel operator to detect Pink ball edges due to overexposure
* Implementation of the SPI protocol in SystemVerilog for fast data transfer to the ESP32
