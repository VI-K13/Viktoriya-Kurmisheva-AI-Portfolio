# Lab 05: CNN-Based Chihuahua vs. Muffin Classification

## Overview

This project explores image classification using a Convolutional Neural Network (CNN) built with PyTorch. I trained a CNN to distinguish between images of Chihuahuas and muffins, continuing the classification task from Lab 04.

The goal was to understand how convolutional layers improve visual feature extraction and how changes in training settings and model architecture affect classification performance.

## Technologies Used

- Python
- PyTorch
- Torchvision
- NumPy
- Matplotlib
- Google Colab

## Dataset

**Dataset:** Chihuahua vs. Muffin Workshop

- **Classes:** Chihuahua and Muffin
- **Training Images:** 120
- **Validation Images:** 30
- **Image Dimensions:** 224 × 224 pixels
- **Image Format:** RGB

The dataset contains separate training and validation folders. Training images were processed using resizing, random horizontal flips, rotations, tensor conversion, and normalization.

**Dataset Source:** [Chihuahua vs. Muffin Workshop](https://github.com/patitimoner/workshop-chihuahua-vs-muffin)

## Project Implementation

The notebook follows a CNN image classification workflow:

1. **Data Preparation:** Loaded the Chihuahua and muffin images using PyTorch ImageFolder and DataLoader.
2. **Image Preprocessing:** Resized and normalized the images, with data augmentation applied during training.
3. **CNN Architecture:** Built a neural network with three convolutional layers containing 32, 64, and 128 output channels.
4. **Feature Extraction:** Used ReLU activation and max pooling to learn and reduce spatial image features.
5. **Model Training:** Trained the CNN for 10 epochs using CrossEntropyLoss and the Adam optimizer.
6. **Model Evaluation:** Evaluated the network on 30 validation images and visualized correct and incorrect predictions.
7. **Parameter Experiments:** Tested changes to training epochs, learning rate, and CNN architecture.

## Personal Experiments

I completed three experiments to investigate how different configurations affect the CNN's performance.

| Configuration | Validation Accuracy |
|---|---:|
| Original CNN (10 Epochs) | 93.33% |
| Reduced Training (5 Epochs) | 80.00% |
| Lower Learning Rate (0.0001) | 90.00% |
| Deeper CNN Architecture | 93.33% |

### Experiment 1: Number of Epochs

I reduced training from 10 epochs to 5 while keeping the original architecture and optimizer settings.

- **Validation Accuracy:** 80.00%
- **Training Time:** 115.01 seconds

The shorter training session resulted in lower validation accuracy than the original CNN.

### Experiment 2: Learning Rate

I lowered the Adam optimizer's learning rate from 0.001 to 0.0001 while keeping 10 training epochs.

- **Validation Accuracy:** 90.00%
- **Training Time:** 228.86 seconds

The smaller learning rate produced slightly lower final validation accuracy than the original model.

### Experiment 3: Deeper CNN Architecture

I added a fourth convolutional layer with 256 output channels and an additional max-pooling layer.

- **Validation Accuracy:** 93.33%
- **Training Time:** 252.14 seconds

The deeper CNN matched the original model's accuracy but required more training time.

## Results and Key Findings

The original CNN achieved **93.33% validation accuracy**, compared with 76.67% for the original fully connected neural network in Lab 04.

During training, the CNN temporarily reached 100% validation accuracy at epoch 7 but finished at 93.33%. This demonstrated that additional training did not consistently improve validation performance.

The experiments showed that:

- Convolutional layers can learn useful spatial features for image classification.
- Reducing training epochs lowered the final validation accuracy in this experiment.
- A lower learning rate did not improve the original CNN's final result.
- Adding more layers did not guarantee higher accuracy.
- More complex networks can require additional computational resources and training time.
- Validation results should be interpreted carefully when using a small dataset.

The CNN made two incorrect predictions on the validation set, both involving Chihuahuas classified as muffins.

## How to Run

1. Open the Jupyter notebook in Google Colab.
2. Run the GitHub cloning cell to download the workshop files and dataset.
3. Install and import the required Python libraries.
4. Load and preprocess the training and validation images.
5. Build and train the original CNN model.
6. Evaluate the model and review its predictions.
7. Run the three additional experiments.
8. Compare the validation accuracy and training time visualizations.

The notebook can run on a CPU, although a GPU may speed up training.

## Acknowledgments

The original workshop materials and dataset are available at [patitimoner/workshop-chihuahua-vs-muffin](https://github.com/patitimoner/workshop-chihuahua-vs-muffin).

The workshop notebook credits Jing Zhao, Dylan Wang, Jason Do, Jason Jiang, and Andrew Jong, along with DeepSense.ai for the original idea and code.

The additional parameter experiments, comparisons, and reflections document my coursework.
