---
title: 'YOLOv11 traning and inference example'
date: 2025-12-01
permalink: /posts/2025/12/yolov11-example/
tags:
  - cool posts
  - category1
  - category2
---

# This post introduce how to install Yolo in general, as well as a simple example about training and inference on a single image. 

## Install

Follow the [Ultralytics YOLO Documents](https://docs.ultralytics.com/) for the installations.

`pip install -U ultralytics`

or

`pip install git+https://github.com/ultralytics/ultralytics.git@main`

![yolo](/images/posts/performance-comparison.png)

## Run it
`python train.py`

## Result

Original Image: 
![Original](/images/posts/bus.jpg)

Detected Image: 
![Detect](/images/posts/bus_detected.jpg)
