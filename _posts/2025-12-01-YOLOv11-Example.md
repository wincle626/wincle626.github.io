---
title: 'YOLOv11 traning and inference example'
date: 2025-12-01
permalink: /posts/2025/12/yolov11-example/
tags:
  - cool posts
  - category1
  - category2
---

# Simple Yolo traning and inference example

## Install

Follow the [Ultralytics YOLO Documents](https://docs.ultralytics.com/) for the installations.

`pip install -U ultralytics`

or

`pip install git+https://github.com/ultralytics/ultralytics.git@main`

![yolo](https://github.com/wincle626/Yolo11_Simple_Example/blob/main/performance-comparison.png)

## Run it
`python train.py`

## Result

Original Image: 
![Original](https://github.com/wincle626/Yolo11_Simple_Example/blob/main/bus.jpg)

Detected Image: 
![Detect](https://github.com/wincle626/Yolo11_Simple_Example/blob/main/runs/detect/predict/bus.jpg)
