# Midterm Project: Smart Recycling Helper

## Overview

Smart Recycling Helper is a proposed computer vision application designed to identify common waste materials from a single photograph.

This project was developed as a Tier 1 image classification blueprint for ITAI 1378. The goal was to design a practical AI solution that could help people recognize waste categories before checking their local recycling and disposal rules.

The midterm focused on project planning, model selection, dataset analysis, system design, and evaluation strategies rather than implementing a complete application.

## Problem Statement

People may struggle to identify which material category an everyday waste item belongs to.

Smart Recycling Helper aims to simplify this process by allowing users to upload a photograph of one item and receive a predicted waste category.

The application is intended to identify materials, not determine whether a specific local recycling program accepts them.

## Proposed Solution

The system was designed to classify waste into six categories:

- Cardboard
- Glass
- Metal
- Paper
- Plastic
- Trash

### Planned Workflow

1. Upload a photograph containing one waste item.
2. Resize and normalize the image.
3. Process the image using a fine-tuned EfficientNet-B0 model.
4. Select the category with the highest prediction score.
5. Display the predicted category and confidence score.

## Technologies and Tools

**Planned development tools:**

- Python
- PyTorch
- Torchvision
- EfficientNet-B0
- Google Colab
- GitHub

**Computer Vision Techniques:**

- Image Classification
- Convolutional Neural Networks (CNNs)
- Transfer Learning
- Image Preprocessing
- Model Evaluation

## Dataset

**Dataset:** [TrashNet](https://github.com/garythung/trashnet)

The proposed training dataset contains 2,527 images across six waste categories.

| Category | Images |
|---|---:|
| Cardboard | 403 |
| Glass | 501 |
| Metal | 410 |
| Paper | 594 |
| Plastic | 482 |
| Trash | 137 |
| **Total** | **2,527** |

### Planned Data Preparation

The proposed workflow includes checking for unreadable images and duplicates, resizing images to 224 × 224 pixels, and using data augmentation during training.

The planned dataset split is:

- Training: 70%
- Validation: 15%
- Testing: 15%

A stratified split would help preserve category representation across the datasets.

## Technical Approach

The proposed system uses transfer learning with a pretrained EfficientNet-B0 convolutional neural network.

The plan involves replacing the model's final classification layer with six outputs and fine-tuning it using TrashNet images.

This approach was selected to make use of pretrained visual features instead of training a neural network entirely from scratch.

## Proposed Success Metrics

The team established three measurable goals for the future implementation.

| Metric | Target |
|---|---|
| Test Accuracy | ≥ 90% |
| Macro F1-score | ≥ 0.85 |
| Average Inference Time | ≤ 1 second per image |

**Note:** These are proposed performance targets, not achieved results. The midterm focused on designing the application rather than training and evaluating the finished model.

## Challenges and Considerations

The project blueprint identified several potential challenges:

- **Similar-looking materials:** Some waste categories may share visual
