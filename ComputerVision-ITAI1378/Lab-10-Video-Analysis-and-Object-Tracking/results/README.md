# Lab 10: Video Analysis and Object Tracking Results

This folder contains visualizations and experimental results from my video object tracking project using YOLOv8n and ByteTrack.

## Results Included

1. **Tracking Timeline Comparison:** Timelines showing tracking IDs across the baseline and modified configurations.
2. **Baseline vs. Modified Tracking:** Side-by-side video frames comparing tracking behavior at selected timestamps.
3. **Restricted-Zone Dwell Time:** A visualization of the monitored zone and the corresponding dwell-time measurements.
4. **Tracking Configuration and Performance:** Results comparing tracking counts, short tracks, and processing times.

## Key Findings

The baseline configuration produced four unique track IDs with no short tracks. After reducing `match_thresh` from 0.8 to 0.5, the modified configuration produced 14 IDs, including eight tracks shorter than one second.

Both runs measured 10.8 seconds of total dwell time across four tracking IDs inside the monitored zone.

Neither configuration consistently met the 100-millisecond processing target needed for analyzing 10 frames per second in real time.

These experiments demonstrated how tracking parameters affect ID consistency and why tracking results require careful evaluation.
