# Lab 10: Video Analysis and Object Tracking Results

This folder contains visualizations and experimental results from my video object tracking project using YOLOv8n and ByteTrack.

## Results Included

1. **[Baseline Tracking Summary](baseline_track_summary.png):** A table showing the four unique tracking IDs, their start and end times, tracking durations, and the number of detection boxes recorded for each track.

2. **[Baseline vs. Modified Tracking](tracking_comparison.png):** Side-by-side video frames comparing tracking behavior at 34.5, 43.5, and 52.5 seconds under two different ByteTrack configurations.

3. **[Restricted-Zone Dwell Time](restricted_zone_dwell_time.png):** A visualization of the monitored zone and the corresponding dwell-time measurements for tracked people.

4. **[Tracking Configuration and Performance](tracking_performance.png):** A record of the tracking settings, parameter changes, unique track counts, and processing-time results.

## Key Findings

The baseline configuration produced four unique track IDs with no tracks shorter than one second. After reducing `match_thresh` from 0.8 to 0.5, the modified configuration produced 14 IDs, including eight short tracks.

Both configurations measured 10.8 seconds of total dwell time across four tracking IDs inside the monitored zone.

The baseline achieved a median processing time of 112.2 ms per frame, compared with 115.0 ms for the modified configuration. Neither consistently met the 100-millisecond target needed to analyze 10 frames per second in real time.

These experiments demonstrated how tracking parameters can affect ID consistency, processing speed, and movement analysis. More tracking IDs do not necessarily mean more people were detected, and tracking results require careful evaluation.
