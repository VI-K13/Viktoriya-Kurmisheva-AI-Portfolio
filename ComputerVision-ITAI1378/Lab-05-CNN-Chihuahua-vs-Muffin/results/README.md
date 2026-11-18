# Lab 05: CNN Classification Results

This folder contains visualizations and experimental results from my CNN-based Chihuahua vs. Muffin image classification project using PyTorch.

## Results Included

1. **Validation Predictions:** A visualization of 30 validation images comparing the CNN's predicted labels with their actual labels.
2. **CNN Accuracy Comparison:** A bar chart comparing validation accuracy across the original CNN and three parameter experiments.
3. **Training Time Comparison:** A visualization comparing the training time required for the three experiments.

## Key Findings

The original CNN achieved 93.33% validation accuracy, improving on the original fully connected model's 76.67% result from Lab 04.

Reducing the number of epochs lowered accuracy to 80.00%, while a lower learning rate resulted in 90.00%. The deeper CNN matched the original accuracy at 93.33% but required 252.14 seconds to train.

These results demonstrate how training settings, computational cost, and network architecture can influence image classification performance.
