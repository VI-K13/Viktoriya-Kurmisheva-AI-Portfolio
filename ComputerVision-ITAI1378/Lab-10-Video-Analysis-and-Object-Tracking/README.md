# Lab 10 (Bonus): Video Analysis and Object Tracking

## Overview

This project explores object tracking in video using YOLOv8n and ByteTrack. I analyzed a video of workers moving through a warehouse to understand how computer vision systems can detect people, assign tracking IDs, and follow movement across multiple frames.

The lab focuses on comparing tracking configurations, analyzing tracking errors, measuring time spent inside a monitored zone, and evaluating processing speed.

## Technologies Used

- Python
- Ultralytics YOLOv8n
- ByteTrack
- OpenCV
- NumPy
- Pandas
- Matplotlib
- PyYAML
- Google Colab

## Video Dataset

**Source:** [Intel Sample Videos](https://github.com/intel-iot-devkit/sample-videos)

**Video:** `worker-zone-detection.mp4`

The experiment used a 30-second section of the video, from 28 to 58 seconds.

- **Video frame rate:** 59.94 FPS
- **Analysis rate:** Approximately 10 FPS
- **Frames analyzed per run:** 300
- **Detection category:** Person

The notebook downloads the sample video automatically.

## Project Implementation

### 1. Video Processing

I loaded the video using OpenCV and selected a 30-second interval for analysis.

Instead of processing every captured frame, I configured the system to analyze approximately 10 frames per second.

This helped me understand the relationship between video frame rate, processing speed, and computational requirements.

### 2. Object Detection and Tracking

I used a pretrained YOLOv8n model to detect people and ByteTrack to associate detections across consecutive frames.

Object detection identifies people in individual frames, while tracking assigns temporary IDs to follow them over time.

These tracking IDs are not personal identities and can change when a tracker loses an object.

### 3. Baseline ByteTrack Configuration

I tested ByteTrack using its default configuration.

**Baseline settings included
