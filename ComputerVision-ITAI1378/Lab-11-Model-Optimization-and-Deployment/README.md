# Lab 11 (Bonus): Model Optimization and Deployment

## Overview

This project explores how to optimize a computer vision model and prepare it for use through an API. I used a pretrained YOLOv8n object detection model to compare inference speed and detection quality at two different input resolutions.

I also built a small detection API using FastAPI, tested valid and invalid image uploads, and verified that the system could switch between model configurations and return to its original settings.

The lab focuses on balancing model speed and detection quality, testing API behavior, and understanding how to deploy computer vision systems more reliably.

## Technologies Used

- Python
- Ultralytics YOLOv8n
- PyTorch
- OpenCV
- NumPy
- Pandas
- Matplotlib
- FastAPI
- FastAPI TestClient
- ONNX and ONNX Runtime
- Google Colab

## Dataset

**Dataset:** COCO8

**Source:** [Ultralytics COCO8](https://docs.ultralytics.com/datasets/detect/coco8/)

The experiment used eight labeled images containing 30 reference objects.

The dataset provided a small test set for comparing object detection performance under different configurations.

The same images, pretrained model weights, confidence threshold, and CPU environment were used for both configurations.

The images were loaded before timing, and the model was warmed up before recording inference times.

## Project Implementation

### 1. Baseline Object Detection

I loaded the pretrained YOLOv8n model and established a baseline using an input image size of 640 pixels.

The baseline configuration used:

- Image size: 640
- Confidence threshold: 0.25
- Device: CPU
- Batch size: 1

I performed 104 timed prediction calls after warming up the model.

### 2. Model Optimization

I created a second configuration by changing only the input image size from 640 to 320 pixels.

All other model settings remained unchanged to make the comparison fair.

### 3. Inference Speed Comparison

I measured median prediction time and the 95th-percentile (p95) latency for both configurations.

| Metric | Baseline (640) | Candidate (320) |
|---|---:|---:|
| Median Latency | 245.5 ms | 79.8 ms |
| P95 Latency | 575.8 ms | 173.8 ms |
| Timed Calls | 104 | 104 |
| Weight File Size | 6.55 MB | 6.55 MB |

Reducing the input size significantly improved processing speed without changing the original model weights.

The 104 timed calls reused eight images, so they provided repeated timing measurements rather than 104 independent examples of detection quality.

### 4. Detection Quality Comparison

I evaluated both configurations against the COCO8 reference annotations using an Intersection over Union (IoU) threshold of 0.5.

| Metric | Baseline (640) | Candidate (320) |
|---|---:|---:|
| Missed Objects | 11 | 18 |
| False Positives | 5 | 7 |

The smaller input size increased missed detections and false positives.

This experiment demonstrated that improving inference speed can come at the cost of detection quality.

### 5. Optional ONNX Export

I completed the optional experiment that exported YOLOv8n from PyTorch to ONNX format.

| Format | File Size |
|---|---:|
| PyTorch | 6.55 MB |
| ONNX | 12.73 MB |

Both versions produced five detection boxes on the same test image at an input size of 320.

This experiment showed that exporting a model to another format does not necessarily reduce its file size.

Matching detection counts on one image provided an initial comparison, but did not establish full prediction equivalence or faster ONNX inference.

### 6. Building a Detection API

I created a FastAPI application to make the object detector accessible through an API interface.

The API included two endpoints:

**GET /health**

Returns information about the active model configuration, including:

- Model version
- Configuration ID
- Input image size
- Readiness status

**POST /v1/detections**

Accepts an uploaded image and returns detected objects, confidence scores, and bounding-box coordinates.

### 7. API Testing

I tested the API using FastAPI's TestClient.

The tests verified that:

- Valid image uploads returned HTTP 200.
- The response included the expected model version.
- The response contained a detections list.
- Invalid image uploads returned HTTP 400.
- Invalid uploads included an error message.

All recorded API checks passed.

The API was tested locally inside the notebook rather than deployed as a public web service.

### 8. Configuration Switching and Rollback

I tested switching the API from the baseline configuration to the smaller input size and then restoring the baseline.

The configurations were identified as:

- Baseline: `cfg-640`
- Candidate: `cfg-320`

After switching back, the API successfully restored the baseline configuration.

All three rollback checks passed:

- The configuration ID matched the baseline.
- The image size returned to 640.
- The test image produced the same detection count as before.

This experiment demonstrated why configuration tracking and rollback testing are important when preparing AI models for deployment.

## Results and Key Findings

The experiments demonstrated several important lessons:

- Reducing input resolution can significantly improve inference speed.
- Faster predictions do not automatically mean better overall performance.
- Smaller input images may cause additional missed detections.
- Model weight size does not change when only the input resolution changes.
- API validation can prevent invalid files from reaching the model.
- Configuration IDs help distinguish different deployments using the same model weights.
- Rollback testing helps verify that a previous working configuration can be restored.
- Model optimization decisions should consider accuracy, speed, reliability, and deployment requirements.

## Deployment Recommendation

Based on my results, I would recommend additional testing before replacing the baseline with the optimized configuration.

Although the smaller input reduced median inference time from 245.5 ms to 79.8 ms, it increased missed detections from 11 to 18 and false positives from 5 to 7.

The experiment used only eight distinct images, so more testing would be necessary to determine whether the speed improvement is worth the reduction in detection quality for a particular application.

## How to Run

1. Open the Jupyter notebook in Google Colab.
2. Install the required Python libraries.
3. Load the pretrained YOLOv8n model.
4. Download and prepare the COCO8 dataset.
5. Run the baseline benchmark using 640-pixel inputs.
6. Run the candidate benchmark using 320-pixel inputs.
7. Compare inference speed and detection quality.
8. Run the optional ONNX export experiment.
9. Generate and test the FastAPI detection service.
10. Switch configurations and execute the rollback tests.
11. Review the benchmark tables, visualizations, and test results.

The notebook runs on a CPU and does not require a GPU, Docker, or a public API endpoint.

An internet connection is required to download the model weights, dataset, and dependencies.

## Acknowledgments

This bonus lab was developed for ITAI 1378 Computer Vision by instructor Patricia McManus.

The notebook contains my completed optimization experiments, API implementation, testing results, deployment decisions, and written reflections.

The pretrained model and COCO8 dataset are provided through Ultralytics.
