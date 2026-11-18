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

**Planned Development Tools:**

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

Training images would receive augmentation such as flips, rotations, and brightness adjustments. Validation data would be used for tuning, while the test set would remain untouched until final evaluation.

More information is available in the [Dataset Preparation Plan](data/README.md).

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

### Planned Evaluation

The proposed evaluation would include:

- Classification accuracy on a held-out test set.
- Precision, recall, and F1-score for each waste category.
- A confusion matrix to identify common classification errors.
- Average inference time for individual images.
- Additional testing using photographs captured in everyday environments.

## Challenges and Considerations

The project blueprint identified several potential challenges:

- **Similar-looking materials:** Some waste categories may share visual characteristics, making classification difficult.
- **Dataset limitations:** Images captured in everyday environments may differ from the training dataset in lighting, angles, and backgrounds.
- **Class imbalance:** The Trash category contains significantly fewer images than other categories.
- **Generalization:** Strong performance on the TrashNet dataset may not guarantee equally reliable predictions on unfamiliar photographs.

The proposed solutions include training augmentation, validation-based model tuning, reviewing class-level performance, and testing with additional real-world photographs.

## Project Development Plan

The midterm proposal outlined five development phases:

| Phase | Planned Work |
|---|---|
| Blueprint | Define the problem, solution, dataset, and technical approach |
| First Working Demo | Test the pretrained model and image-processing pipeline |
| Make It Yours | Fine-tune EfficientNet-B0 and develop the classification interface |
| Improve and Measure | Evaluate predictions, tune parameters, and measure performance |
| Package and Present | Prepare the final demonstration, documentation, and presentation |

These milestones describe the planned development process rather than completed implementation.

## Project Outcome

The completed midterm deliverables included a project proposal, technical workflow, dataset plan, success criteria, milestone schedule, and supporting GitHub documentation.

This project helped me practice designing a computer vision application before implementation, including selecting appropriate technologies, defining project scope, identifying limitations, and planning how to evaluate the system.

The midterm resulted in a documented project blueprint, not a trained or deployed waste-classification model.

## Team and Contributions

Smart Recycling Helper was developed as a group project for ITAI 1378.

The original team repository credits:

- Viktoriya Kurmisheva
- Abraham Barreto
- Tien Manh Nguyen

### My Contribution

I contributed to the project concept, prepared the introductory proposal slides explaining the problem and proposed workflow, and created the original GitHub repository.

I organized project documentation, worked on the dataset preparation plan, and explored how TrashNet, EfficientNet-B0, PyTorch, and transfer learning would fit the proposed solution.

I also documented my use of AI tools during the planning process, including the decisions I made and the concepts I learned.

My individual AI assistance record is available in the [AI Usage Log](docs/AI_usage_log.md).

## Project Files

| File | Description |
|---|---|
| [Midterm Proposal (PDF)](MD_FishVision_Viktoriya_ITAI1378.pdf) | Nine-page presentation explaining the proposed Smart Recycling Helper system |
| [Dataset Preparation Plan](data/README.md) | TrashNet dataset information, planned preprocessing steps, data splitting, and limitations |
| [AI Usage Log](docs/AI_usage_log.md) | Documentation of my AI assistance, decisions, contributions, and learning experience |
| [Original Team Repository](https://github.com/VI-K13/Midterm_ITAI_1378_smart-recycling-helper_proposal) | Original collaborative project repository and supporting documentation |

## References

- [TrashNet Dataset — Gary Thung and Mindy Yang](https://github.com/garythung/trashnet)
- [EfficientNet-B0 — PyTorch Documentation](https://docs.pytorch.org/vision/stable/models/generated/torchvision.models.efficientnet_b0.html)
