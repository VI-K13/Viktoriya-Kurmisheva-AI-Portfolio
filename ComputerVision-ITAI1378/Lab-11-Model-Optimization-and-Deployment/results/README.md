# Lab 11: Model Optimization and Deployment Results

This folder contains visualizations and test results from my YOLOv8n model optimization and FastAPI deployment experiments.

## Results Included

1. **Inference Latency Comparison:** A box plot comparing prediction times using 640- and 320-pixel input images.
2. **Optimization Results:** A table comparing latency, missed objects, false positives, and model size.
3. **Detection Comparison:** Side-by-side object detection results from the baseline and optimized configurations.
4. **API Test Results:** Outputs showing successful validation of image uploads and API responses.
5. **Configuration Rollback:** Test results confirming the successful restoration of the original model configuration.

## Key Findings

Reducing the input image size from 640 to 320 lowered the median inference time from 245.5 ms to 79.8 ms.

However, missed detections increased from 11 to 18, and false positives increased from five to seven on the same eight-image test set.

The FastAPI tests successfully handled valid and invalid image uploads. The rollback experiment restored the original configuration, and all three verification checks passed.

These results demonstrated the tradeoff between inference speed and detection quality, along with the importance of testing and rollback procedures when preparing computer vision models for deployment.
