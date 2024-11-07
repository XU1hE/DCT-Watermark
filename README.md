# DCT-Watermark：Invisible Digital Watermarking for Image Protection

## Overview

This repository contains a project focused on **Invisible Digital Watermarking** for image protection. The goal of this project is to implement a method for embedding an invisible watermark in an image, which ensures copyright protection and prevents unauthorized usage or tampering. The watermark is designed to be robust against common image transformations, such as compression, resizing, and noise addition.

**Project Members**:
- Xu Y.
- Huang Q.
- Xiang M.
- Chen K.

**Course**: Digital Image Processing (DIP)

**Date**: November 6, 2024

## Project Goals

- **Watermark Embedding**: Embed a robust, invisible digital watermark into an image to protect copyright.
- **Robustness Testing**: Test the watermark's resilience against common image manipulations (e.g., compression, noise addition, resizing).
- **Watermark Extraction**: Demonstrate the extraction of the watermark from tampered images to verify ownership.

## Key Techniques

- **Discrete Cosine Transform (DCT)**: Used for embedding the watermark in the frequency domain of the image, ensuring it is invisible in the spatial domain.
- **Arnold Transformation**: Scrambles the watermark image to add an extra layer of security.
- **Template Matching**: Used for watermark accuracy evaluation after image manipulation.

## Directory Structure
. ├── input_image.jpg # Input image to be watermarked ├── custom_watermark.jpg # Custom watermark image ├── modified_images/ # Folder to store images modified with transformations ├── regenerated_watermarks/ # Folder to store extracted watermarks ├── watermarked_image.jpg # Output image with the embedded watermark └── README.md # Project README

