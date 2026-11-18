# Lab 09 (Bonus): Build a Visual Monitoring Agent

## Overview

This project explores how computer vision can be used to create a visual monitoring agent for workplace safety. I used a pretrained YOLOv8n object detection model and Python rules to monitor video frames, identify people, and generate alerts when specific conditions were met.

The lab focuses on the Perception, Reasoning, Action (PRA) loop, agent memory, restricted-zone monitoring, decision logging, and human-review safeguards.

## Technologies Used

- Python
- Ultralytics YOLOv8n
- OpenCV
- NumPy
- Matplotlib
- Google Colab

## Video Data

The project uses two sample videos from Intel's public sample-video repository:

- **Worker Zone Detection:** Used for monitoring people and testing restricted-zone alerts.
- **Store Aisle Detection:** Used for testing uncertain detections, human-review decisions, and monitoring a different object category.

**Video Source:** [Intel Sample Videos](https://github.com/intel-iot-devkit/sample-videos)

The notebook downloads the videos automatically, so they do not need to be uploaded separately.

## Project Implementation

### 1. Perception, Reasoning, Action (PRA) Loop

I created a basic visual monitoring agent with three main functions:

- **Perception:** `perceive()` uses YOLOv8n to detect objects in video frames.
- **Reasoning:** `reason()` evaluates detections using object labels and confidence thresholds.
- **Action:** `act()` prints alerts and records them in a log.

The `run_agent()` function repeats these steps while processing video frames.

### 2. Basic Object Monitoring

I tested the agent on a workplace video to detect people.

The basic agent generated **57 alerts during a 20-second video interval**.

Because the agent checked frames repeatedly, it produced multiple alerts while people remained visible.

### 3. Short-Term Memory

I added a five-second cooldown to prevent the agent from repeatedly reporting detections within a short period.

| Configuration | Alerts |
|---|---:|
| Basic Agent | 57 |
| Agent with Memory | 4 |

Both tests used the same 20-second video interval.

The cooldown reduced repeated notifications, making the monitoring system less disruptive.

### 4. Restricted-Zone Monitoring

I implemented a rectangular restricted zone in the workplace video.

The agent checks the bottom-center point of each person's bounding box to determine whether that person is inside the zone.

The restricted-zone test produced **37 alerts during a 40-second interval**.

This experiment demonstrated how location-based reasoning can make alerts more specific.

The zone test and the basic test used different video durations, so their alert counts are not directly comparable.

### 5. ReAct-Style Decision Logging

I implemented a decision log that records the agent's plan, action, observation, and decision.

The agent evaluates detected people using three confidence-based decisions:

- **ALERT:** Confidence of 0.60 or higher.
- **HUMAN_REVIEW:** Confidence from 0.30 to below 0.60.
- **IGNORE:** Confidence below 0.30.

The experiment on the store video produced:

| Decision | Count |
|---|---:|
| ALERT | 106 |
| HUMAN_REVIEW | 8 |
| IGNORE | 7 |

These counts represent decisions on detection candidates rather than confirmed safety incidents.

The human-review category flags uncertain detections for review instead of treating every prediction as reliable.

### 6. Monitoring a Different Object

I tested the agent with a different COCO object category: **cup**.

The model recognized cup as a valid class, but the experiment generated zero alerts in the selected store video interval.

This demonstrated that a supported object category does not guarantee successful detection in every environment.

## Results and Key Findings

The experiments demonstrated how a basic object detector can become a more useful monitoring agent by combining computer vision with reasoning rules, memory, and decision logging.

I learned that:

- The PRA loop connects object detection with decisions and actions.
- Confidence thresholds help filter uncertain detections.
- Short-term memory reduces repeated alerts.
- Restricted zones allow more targeted monitoring.
- Human-review rules help identify cases requiring additional attention.
- Small or partially hidden objects can be difficult to detect.
- Monitoring systems should consider privacy, false alarms, and human oversight.

## Potential Real-World Application

I explored the idea of creating a monitoring agent for a robotics laboratory.

The proposed system would detect people near moving robots, check whether they entered restricted areas, and generate safety warnings.

It could use short-term memory to reduce repeated alerts and request instructor review when the situation was uncertain.

This application was proposed as a future idea rather than implemented in the notebook.

## How to Run

1. Open the Jupyter notebook in Google Colab.
2. Install Ultralytics and OpenCV.
3. Load the pretrained YOLOv8n model.
4. Download the two sample videos using the setup cells.
5. Run the basic monitoring agent.
6. Test the memory cooldown and restricted-zone rules.
7. Execute the ReAct-style decision logging experiment.
8. Run the additional object-monitoring experiment.
9. Review the generated alerts, annotated video frames, and logs.

An internet connection is required to download the pretrained model and sample videos.

## Acknowledgments

This bonus lab was developed for ITAI 1378 Computer Vision by instructor Patricia McManus.

The notebook includes my completed coding exercises, experiments, observations, and written reflections.

The object detection model is provided through Ultralytics, and the sample videos come from Intel's public sample-video collection.
