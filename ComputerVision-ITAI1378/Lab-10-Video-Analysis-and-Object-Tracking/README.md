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

**Baseline settings included:**

- `match_thresh`: 0.8
- `track_buffer`: 30
- `track_high_thresh`: 0.25

The baseline produced:

- **4 unique track IDs**
- **0 short tracks under one second**
- **112 ms median processing time per frame**

### 4. Modified Tracking Configuration

I changed only one parameter to investigate its effect on tracking performance.

| Parameter | Baseline | Modified |
|---|---:|---:|
| `match_thresh` | 0.8 | 0.5 |

All other settings remained unchanged.

The modified configuration produced:

- **14 unique track IDs**
- **8 short tracks under one second**
- **115 ms median processing time per frame**

The lower matching threshold produced more fragmented tracking results in this experiment.

### 5. Tracking Comparison

I compared the baseline and modified tracking configurations at three timestamps:

- **34.5 seconds:** The baseline tracked two workers, while the modified configuration tracked only one.
- **43.5 seconds:** Both configurations tracked one worker, using different IDs.
- **52.5 seconds:** Both configurations tracked one worker, again using different IDs.

These comparisons demonstrated how changing tracking parameters can affect object association and tracking consistency.

The results did not establish which configuration was more accurate across every frame.

### 6. Restricted-Zone Dwell Time

I created a rectangular monitoring zone and measured how long tracked people remained inside it.

The system used the bottom-center point of each person's bounding box to determine whether the track entered the zone.

| Measurement | Baseline | Modified |
|---|---:|---:|
| Track IDs inside zone | 4 | 4 |
| Total measured dwell time | 10.8 seconds | 10.8 seconds |

Both configurations produced the same total dwell time, although they assigned different tracking IDs.

This showed that identical summary measurements do not necessarily mean two tracking configurations behave identically.

### 7. Processing Speed

I measured the median and 95th-percentile processing times for both configurations.

| Configuration | Median Time | 95th Percentile |
|---|---:|---:|
| Baseline | 112.2 ms | 183.4 ms |
| Modified | 115.0 ms | 185.8 ms |

At 10 analyzed frames per second, the system needs to process each frame within approximately 100 milliseconds to keep up consistently.

Neither configuration consistently met this target.

## Results and Key Findings

The experiments demonstrated that:

- Object detection and tracking serve different purposes.
- Tracking IDs can change or become fragmented.
- Changing a single ByteTrack parameter can significantly affect tracking results.
- More track IDs do not necessarily indicate more people.
- Tracking errors can affect movement and dwell-time reports.
- A system that processes video successfully does not automatically operate in real time.
- Human verification is important when tracking results could affect workplace decisions.

The modified configuration produced more track IDs and short tracks without showing a clear improvement over the baseline.

## Practical Applications and Limitations

Object tracking can support warehouse monitoring, movement analysis, restricted-zone detection, and activity measurement.

However, tracking errors can lead to misleading reports. I would not recommend using this system alone to evaluate employee performance without more testing and human review.

The experiment was limited to a single 30-second video clip without ground-truth tracking identities.

## How to Run

1. Open the Jupyter notebook in Google Colab.
2. Install Ultralytics, OpenCV, and the required tracking dependencies.
3. Download the Intel worker-zone video.
4. Load the pretrained YOLOv8n model.
5. Run the baseline ByteTrack configuration.
6. Change the matching threshold and repeat the experiment.
7. Compare the tracking timelines and selected video frames.
8. Calculate dwell times inside the restricted zone.
9. Review the processing-time measurements and configuration record.

The notebook requires an internet connection for downloading the video and model weights.

## Acknowledgments

This bonus lab was developed for ITAI 1378 Computer Vision by instructor Patricia McManus.

The notebook contains my completed tracking experiments, code, observations, and written reflections.

The pretrained detection model and ByteTrack implementation are provided through Ultralytics, and the sample video comes from Intel's public sample-video repository.
