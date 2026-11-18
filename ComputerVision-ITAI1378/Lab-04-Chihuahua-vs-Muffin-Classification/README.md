# Lab 04: Chihuahua vs. Muffin Image Classification

## Overview

This project explores image classification using a neural network built with PyTorch. I worked with a model called MySkynet to classify images of Chihuahuas and muffins, two categories that can sometimes look surprisingly similar.

The workshop focuses on neural network architecture, image preprocessing, model training, validation, and improving classification performance through parameter experimentation.

## Technologies Used

- Python
- PyTorch
- Torchvision
- NumPy
- Matplotlib
- Pillow (PIL)
- Google Colab

## Dataset

The project uses a Chihuahua vs. Muffin image dataset from the original workshop.

- **Classes:** Chihuahua and Muffin
- **Training images:** 120
- **Validation images:** 30
- **Original processing size:** 224 × 224 pixels
- **Image format:** RGB

The notebook downloads the workshop repository containing the training and validation images.

**Dataset and Workshop Source:** [Chihuahua vs. Muffin Workshop](https://github.com/patitimoner/workshop-chihuahua-vs-muffin)

## Project Implementation

The lab follows a neural network classification workflow:

1. **Data Preparation:** Loaded images from separate training and validation folders.
2. **Image Preprocessing:** Resized images, converted them into tensors, and normalized their pixel values.
3. **Neural Network Architecture:** Used MySkynet, a fully connected neural network that flattens RGB images before passing them through Linear layers.
4. **Model Training:** Trained the network using CrossEntropyLoss and the SGD optimizer.
5. **Model Evaluation:** Monitored training loss, accuracy, and validation performance.
6. **Prediction Visualization:** Displayed validation images alongside model outputs.
7. **Parameter Experiments:** Tested six modifications to evaluate their effects on model accuracy.

## Personal Experiments

I conducted six experiments to understand how different training settings affect classification performance.

| Experiment | Validation Accuracy |
|---|---:|
| Original Model (Baseline) | 76.67% |
| Increased Training Epochs | 93.33% |
| Lower Learning Rate | 90.00% |
| Changed Optimizer to Adam | 76.67% |
| Modified Network Layers | 73.33% |
| Reduced Image Size | 86.67% |
| Added Data Augmentation | 76.67% |

### Experiment Details

**1. Number of Epochs**

Increased training from 3 to 10 epochs while keeping the original architecture and optimizer. This achieved the highest validation accuracy of 93.33%.

**2. Learning Rate**

Reduced the SGD learning rate from 0.1 to 0.01, achieving 90.00% validation accuracy.

**3. Optimizer Type**

Replaced SGD with Adam using a learning rate of 0.001. The resulting accuracy was 76.67%.

**4. Network Architecture**

Modified the number and dimensions of the Linear layers. This configuration achieved 73.33% accuracy.

**5. Image Size**

Reduced the input image dimensions from 224 × 224 to 128 × 128 pixels. The model achieved 86.67% accuracy.

**6. Data Augmentation**

Added random horizontal flips and small rotations to the training images. The resulting validation accuracy was 76.67%.

## Results and Key Findings

The original MySkynet model achieved 76.67% validation accuracy. Increasing the number of training epochs produced the best result at 93.33%.

The experiments demonstrated that:

- Training parameters can significantly influence model performance.
- More training epochs improved accuracy in this experiment.
- Lowering the learning rate improved validation performance.
- Increasing network complexity did not automatically improve accuracy.
- Image size and data augmentation can influence classification results.
- Comparing experiments requires consistent evaluation conditions.

This lab helped me understand how image preprocessing, neural network training, and parameter tuning contribute to computer vision applications.

## How to Run

1. Open the Jupyter notebook in Google Colab.
2. Run the import and model setup cells.
3. Execute the GitHub cloning cell to download the workshop files and dataset.
4. Load and preprocess the training and validation images.
5. Train and evaluate the original MySkynet model.
6. Run the six experiments.
7. Review the validation accuracy comparison chart.

A GPU is recommended for faster training.

## Acknowledgments

The original Chihuahua vs. Muffin workshop, including its initial MySkynet implementation and supporting materials, was created by Jing Zhao, Dylan Wang, Jason Do, Jason Jiang, and Andrew Jong, with credit to DeepSense.ai for the original idea and code.

The additional parameter experiments and comparisons document my coursework.
