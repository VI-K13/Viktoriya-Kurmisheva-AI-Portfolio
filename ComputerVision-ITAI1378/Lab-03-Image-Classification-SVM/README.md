# Lab 03: Image Classification with SVM

## Overview

This project explores image classification using traditional machine learning techniques. I used the CIFAR-10 dataset to train and evaluate a Support Vector Machine (SVM) classifier that distinguishes between three image categories: cats, dogs, and ships.

The lab demonstrates how image preprocessing, feature extraction, and model configuration influence classification performance.

## Technologies Used

- Python
- NumPy
- Matplotlib
- Scikit-learn
- TensorFlow/Keras (dataset loading)
- Google Colab

## Dataset

**Dataset:** CIFAR-10

**Selected Classes:** Cat, Dog, Ship

- Training images: 15,000
- Testing images: 3,000
- Original image dimensions: 32 × 32 pixels
- Features after preprocessing: 1,024 per image

The dataset was loaded using TensorFlow/Keras and filtered to include only the three selected categories.

**Dataset Source:** https://www.cs.toronto.edu/~kriz/cifar.html

## Project Implementation

The notebook follows a supervised machine learning workflow:

1. **Data Preparation:** Loaded the CIFAR-10 dataset and selected three image classes.
2. **Image Preprocessing:** Converted images to grayscale and normalized pixel values.
3. **Feature Extraction:** Flattened each image into 1,024 numerical features.
4. **Model Training:** Trained a Linear SVM using Scikit-learn.
5. **Model Evaluation:** Measured classification accuracy, precision, recall, and F1-score.
6. **Prediction Visualization:** Compared actual image labels with the model's predictions.

## Personal Experiments

After completing the original classifier, I conducted three experiments to investigate factors affecting model performance.

### Experiment 1: Linear vs. RBF Kernels

I trained two SVM models using the same balanced sample of 3,000 training images to compare linear and nonlinear decision boundaries.

| Kernel | Accuracy |
|---|---|
| Linear | 50.67% |
| RBF | 62.00% |

The RBF kernel performed better on this sample, suggesting that nonlinear decision boundaries were more effective for these image features.

### Experiment 2: Changing the C Parameter

I tested how changing the SVM regularization parameter affected classification accuracy using the full training dataset.

| C Value | Accuracy |
|---|---|
| 1.0 | 54.70% |
| 0.1 | 55.93% |

Reducing C produced a small improvement in model accuracy.

### Experiment 3: Training Dataset Size

I compared a Linear SVM trained on the full dataset with one trained on half of the available images.

| Training Images | Accuracy |
|---|---|
| 15,000 | 54.70% |
| 7,500 | 52.77% |

Reducing the training dataset size decreased accuracy, demonstrating how the amount of available training data can affect model performance.

## Results and Key Findings

The original Linear SVM achieved **54.70% accuracy** on the 3,000 test images.

Ships were classified more accurately than cats and dogs, reaching an F1-score of 0.67. Cats and dogs had lower F1-scores of approximately 0.48–0.49.

The additional experiments demonstrated that:

- Kernel selection can significantly affect classification performance.
- Changing regularization strength can influence model accuracy.
- Reducing training data may lower classification performance.
- Fair comparisons require consistent experimental conditions.
- Computational limitations can affect how machine learning experiments are designed.

The RBF model achieved the highest accuracy in the experiments at 62.00%, using the smaller 3,000-image training sample.

## How to Run

1. Open the Jupyter notebook in Google Colab.
2. Run the installation and import cells.
3. Load the CIFAR-10 dataset using TensorFlow/Keras.
4. Execute the preprocessing and model training cells.
5. Review the classification results and visualizations.
6. Run the additional experiments to compare SVM configurations.

The dataset downloads automatically through Keras, so no manual dataset download is required.
