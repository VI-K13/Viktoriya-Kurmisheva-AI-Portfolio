# Lab 08: Vision Transformers and Vision Language Models

## Overview

This project explores how Vision Transformers (ViTs) and Vision Language Models (VLMs) process visual information and respond to natural-language questions.

I used SmolVLM-500M-Instruct to experiment with image descriptions, visual question answering, object classification, counting, accessibility alt text, and chart reading. I also tested the model's reliability by asking misleading questions and conducting a workplace deployment audit.

The lab focuses on understanding how prompts affect a model's behavior and why its responses need to be evaluated before being used in real-world applications.

## Technologies Used

- Python
- PyTorch
- Hugging Face Transformers
- SmolVLM-500M-Instruct
- SmolVLM-256M-Instruct
- Pillow (PIL)
- Matplotlib
- Google Colab

## Models Used

**Primary Model:** [SmolVLM-500M-Instruct](https://huggingface.co/HuggingFaceTB/SmolVLM-500M-Instruct)

**Bonus Model:** [SmolVLM-256M-Instruct](https://huggingface.co/HuggingFaceTB/SmolVLM-256M-Instruct)

Both models were loaded through Hugging Face Transformers.

## Project Implementation

### 1. Vision Transformer Patch Visualization

I explored how images can be divided into patches using a dog image.

I compared two patch sizes:

- **48 × 48 pixels:** 64 image patches
- **96 × 96 pixels:** 16 image patches

Smaller patches preserved more individual visual details but required more pieces to represent the image.

The patch grids were visual demonstrations rather than direct measurements of the VLM's internal image processing.

### 2. Visual Question Answering

I used SmolVLM-500M-Instruct to answer three questions of increasing difficulty about a cat image.

The questions focused on object recognition, visual details, and interpreting the animal's apparent mood.

The model successfully recognized the cat but gave a less complete answer when asked to explain its interpretation of the cat's feelings.

### 3. One Model, Multiple Tasks

I tested how changing the prompt allowed the same VLM to perform different computer vision tasks:

- Image classification
- Object counting
- Object description

The model identified the cat, counted one cat, and described other visible elements in the image.

### 4. Accessibility Alt Text

I tested basic and professionally structured prompts on cat and dog images.

The professional prompts produced shorter, more focused descriptions. However, some important details were missing, showing why human review remains necessary.

### 5. Chart Reading

I created a food truck sales chart with known monthly values and asked the model three questions.

The model correctly identified March sales as 140 units and selected June as the highest-sales month, using the abbreviated answer "Jun."

However, it incorrectly reported that sales increased from April to May.

The notebook's strict text-matching code recorded 1/3 correct, while a meaning-based evaluation gives 2/3 correct because "Jun" and "June" refer to the same month.

### 6. Hallucination Testing

I designed misleading questions to test whether the model would recognize information that was absent from an image.

The model correctly rejected several false assumptions. However, when asked why sales dropped in July, it invented a COVID-19 explanation even though the chart only contained data from January through June.

This experiment demonstrated how a VLM can generate convincing but unsupported information.

## Independent Project: Retail Product Description Audit

I conducted a small workplace reliability audit using two product images: a red sneaker and a backpack.

I tested three differently worded prompts for each image to determine whether the model could produce consistent online store descriptions.

### Findings

- The model recognized the sneaker and described some visible features.
- Responses became less detailed when prompts changed.
- The model recognized the backpack but sometimes focused on the person's clothing instead of the product.
- Similar prompts did not consistently produce equally useful descriptions.

**Recommendation:** Use the model with human review rather than publishing product descriptions automatically.

## Bonus Experiments

### Bonus A: Comparing Model Sizes

I compared SmolVLM-500M-Instruct with SmolVLM-256M-Instruct using the same three questions about the cat image.

The smaller model correctly identified the animal and its eye color, but the two models gave different interpretations of the cat's mood.

### Bonus B: Receipt Reading

I created a sample store receipt using Pillow and tested whether the smaller VLM could extract numerical information.

The model correctly read:

- Total price: $8.50
- Pencil price: $1.25

However, it returned full sentences instead of following the requested answer-only format.

### Bonus C: Patch-Size Experiment

I displayed the receipt using a 96-pixel patch grid and asked the model to identify the eraser's price.

The model correctly returned $2.75 despite the small text.

This experiment illustrated the difficulty of interpreting fine visual details and the importance of distinguishing patch visualizations from actual model processing.

## Results and Key Findings

This lab demonstrated that:

- Smaller image patches can represent finer visual details.
- A single VLM can perform multiple tasks through prompting.
- Prompt wording can affect the quality and consistency of responses.
- VLMs can correctly extract information while still making reasoning errors.
- Models may hallucinate explanations that are unsupported by the image.
- Human review remains important for accessibility, document processing, and retail applications.
- Smaller VLMs can perform useful tasks but have limitations.

## How to Run

1. Open the Jupyter notebook in Google Colab.
2. Select a T4 GPU if available.
3. Install the required Hugging Face libraries.
4. Run the image patch visualization cells.
5. Load SmolVLM-500M-Instruct.
6. Execute the visual question answering and prompting experiments.
7. Run the chart-reading, hallucination, and reliability tests.
8. Complete the optional smaller-model and receipt-reading experiments.

The notebook requires an internet connection to download model weights and external images.

## Acknowledgments

This lab was developed for ITAI 1378 by instructor Patricia McManus, with Claude (Anthropic) credited as a collaborator in the course notebook.

The independent experiments, observations, reliability audit, and written responses document my completed coursework.
