# Lab 02: Image Processing Fundamentals

## Overview

This project explores how computers represent and process digital images using Python. I worked with pixel values, color channels, filters, and geometric transformations to understand how mathematical operations affect an image's appearance and information.

The lab focuses on traditional image processing techniques and how they relate to modern computer vision applications.

## Technologies Used

- Python
- OpenCV
- NumPy
- Pillow (PIL)
- Matplotlib
- Google Colab

## Project Implementation

The notebook covers several image processing techniques:

- **Image Representation:** Exploring pixel values, image dimensions, and RGB color channels.
- **Grayscale Conversion:** Converting color images into grayscale.
- **Brightness and Contrast:** Adjusting pixel intensities and observing their effects.
- **Convolution Filters:** Applying blurring, sharpening, and edge detection.
- **Histogram Enhancement:** Exploring histogram equalization and CLAHE.
- **Geometric Transformations:** Applying scaling, rotation, translation, perspective transformations, and shearing.
- **Creative Effects:** Combining traditional processing operations to create different visual styles.

## Personal Experiments

I expanded the lab with four additional experiments:

1. **Brightness and Clipping:** Compared two brightness adjustments to examine how stronger increases can cause pixel clipping.
2. **Custom Emboss Filter:** Created a convolution kernel that produces a raised-edge effect.
3. **CLAHE Comparison:** Tested different clip limits to compare their effects on image contrast.
4. **Noise Reduction:** Added salt-and-pepper noise and applied median filtering to reduce it.

## Results and Key Findings

The experiments demonstrated how different image processing operations can change the appearance and numerical properties of an image.

I found that stronger adjustments do not always produce better results. Brightness increases can cause clipping, and changing CLAHE parameters does not always improve contrast. The median filtering experiment demonstrated how effectively noise can be reduced.

These experiments helped me better understand the relationship between image processing and computer vision.

## How to Run

1. Open the Jupyter notebook in Google Colab.
2. Run the setup cell to install and import the required libraries.
3. Execute the remaining cells in order.
4. Review the generated images, visualizations, and experimental results.

The notebook generates its own sample image, so no external dataset is required.
