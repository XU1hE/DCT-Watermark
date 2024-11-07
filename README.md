# DCT-Robustness: Invisible Digital Watermarking for Image Protection

## Table of Contents

- [Overview](#overview)
- [Project Structure](#project-structure)
- [How to Run the Project](#how-to-run-the-project)
- [Functions Overview](#functions-overview)
- [Example Workflow](#example-workflow)
- [Image Transformations](#image-transformations)
- [Conclusion](#conclusion)
- [License](#license)
- [Contact](#contact)

## Overview

This repository contains a project focused on **Invisible Digital Watermarking** for image protection. The goal of this project is to implement a method for embedding an invisible watermark in an image, which ensures copyright protection and prevents unauthorized usage or tampering. The watermark is designed to be robust against common image transformations, such as compression, resizing, and noise addition. This is a Digital Image Process (2024-2025) course  Project.

**Project Members**:
- Xu Y.
- Huang Q.
- Xiang M.
- Chen K.


## Project Goals

- **Watermark Embedding**: Embed a robust, invisible digital watermark into an image to protect copyright.
- **Robustness Testing**: Test the watermark's resilience against common image manipulations (e.g., compression, noise addition, resizing).
- **Watermark Extraction**: Demonstrate the extraction of the watermark from tampered images to verify ownership.

## Key Techniques

- **Discrete Cosine Transform (DCT)**: Used for embedding the watermark in the frequency domain of the image, ensuring it is invisible in the spatial domain.
- **Arnold Transformation**: Scrambles the watermark image to add an extra layer of security.
- **Template Matching**: Used for watermark accuracy evaluation after image manipulation.

## Directory Structure

- **`input_image.jpg`**: The input image that will have the watermark applied.
- **`custom_watermark.jpg`**: The custom image that will serve as the watermark.
- **`modified_images/`**: A folder to store images that have been altered with various transformations, such as noise or resizing.
- **`regenerated_watermarks/`**: A folder to store watermarks that have been extracted from the modified images.
- **`watermarked_image.jpg`**: The resulting image with the watermark applied.
- **`README.md`**: This file, providing details and instructions for the project.


## Requirements

The project requires the following Python libraries:

- `numpy`
- `scipy`
- `PIL` (Pillow)
- `opencv-python`
- `matplotlib`

Install the necessary dependencies using `pip`:

```bash
pip install numpy scipy pillow opencv-python matplotlib
```

## How to Run the Project

### Clone the repository:

```bash
git clone https://github.com/yourusername/invisible-digital-watermarking.git
cd invisible-digital-watermarking
```

## Functions Overview
- **`arnold_transform(img, iterations)`**: Applies Arnold transformation to scramble the watermark image for additional security.
dct2(image) and idct2(image): Perform Discrete Cosine Transform (DCT) and its inverse (IDCT) on image blocks.
embed_watermark(image, watermark, A, watermark_scale): Embeds the watermark into the image using DCT.
extract_watermark(watermarked_image, original_image): Extracts the watermark from the watermarked image.
imageVSwatermark_accuracy(image_index, template, inverted_template): Evaluates the accuracy of the extracted watermark using template matching.
