# DCT-Watermark: Invisible Digital Watermarking for Image Protection

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

This project demonstrates the use of invisible digital watermarking for image protection. The goal is to embed a watermark into an image such that it remains undetectable to the human eye but can be extracted after any image manipulation or tampering. In this project, we use the Discrete Cosine Transform (DCT) for embedding and extracting the watermark, making the process robust against typical image transformations. This is a course project for UESTC4035: Digital Image Processing (2024-2025).


## Project Structure

- **`DCT-Watermark.ipynb`**: The main script for the project, implementing the DCT-based watermarking algorithm.
- **`input_image.jpg`**: The input image that will have the watermark applied.
- **`custom_watermark.jpg`**: The custom image that will serve as the watermark.
- **`modified_images/`**: A folder to store images that have been altered with various transformations, such as noise or resizing.
- **`regenerated_watermarks/`**: A folder to store watermarks that have been extracted from the modified images.
- **`watermarked_image.jpg`**: The resulting image with the watermark applied.
- **`README.md`**: This file, providing details and instructions for the project.


## How to Run the Project

### Clone the repository:

```bash
git clone https://github.com/yourusername/invisible-digital-watermarking.git
cd invisible-digital-watermarking
```

### Install the required libraries:

```bash
pip install numpy scipy pillow opencv-python matplotlib
```

### Execute the script: 

DCT-Watermark.ipynb


## Functions Overview
- **`arnold_transform(img, iterations)`**: Applies Arnold transformation to scramble the watermark image for additional security.
- **`dct2(image) and idct2(image)`**: Perform Discrete Cosine Transform (DCT) and its inverse (IDCT) on image blocks.
- **`embed_watermark(image, watermark, A, watermark_scale)`**: Embeds the watermark into the image using DCT.
- **`extract_watermark(watermarked_image, original_image)`**: Extracts the watermark from the watermarked image.
- **`imageVSwatermark_accuracy(image_index, template, inverted_template)`**: Evaluates the accuracy of the extracted watermark using template matching.
