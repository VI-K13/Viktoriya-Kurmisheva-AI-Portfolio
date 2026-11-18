# Lab 09: Visual Monitoring Agent Results

This folder contains screenshots and experimental outputs from my visual monitoring agent built with YOLOv8n and Python.

## Results Included

1. **Basic Agent Detection:** Annotated video frames showing detected people and object bounding boxes.
2. **Memory Comparison:** Alert logs demonstrating the effect of adding a five-second cooldown.
3. **Restricted-Zone Monitoring:** A visualization of the rectangular monitoring zone used for location-based alerts.
4. **Human Review and Decision Log:** Confidence-based decisions categorized as ALERT, HUMAN_REVIEW, or IGNORE.

## Key Findings

The basic monitoring agent generated 57 alerts during a 20-second video interval. Adding a five-second cooldown reduced this to four alerts over the same interval.

The restricted-zone experiment generated 37 alerts during a separate 40-second test.

The human-review experiment recorded 106 ALERT decisions, eight HUMAN_REVIEW decisions, and seven IGNORE decisions.

These experiments showed how memory, restricted-zone rules, and confidence-based decision making can improve the usefulness of a visual monitoring system while highlighting the importance of human oversight.
