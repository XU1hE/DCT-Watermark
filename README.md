# DCT-Watermark: Invisible Digital Watermarking for Image Protection

## Table of Contents

- [Overview](#overview)
- [Project Structure](#project-structure)
- [How to Run the Project](#how-to-run-the-project)
- [Functions Overview](#functions-overview)
- [Image Transformations](#image-transformations)
- [Conclusion](#conclusion)
- [License](#license)
- [Contact](#contact)

## Overview

This project demonstrates the use of invisible digital watermarking for image protection. The goal is to embed a watermark into an image such that it remains undetectable to the human eye but can be extracted after any image manipulation or tampering. In this project, we use the Discrete Cosine Transform (DCT) for embedding and extracting the watermark, making the process robust against typical image transformations. This is a course project for UESTC4035: Digital Image Processing (2024-2025).


## Project Structure

```bash
modified_images/          - A folder to store images altered with various transformations (e.g., noise, resizing).
regenerated_watermarks/   - A folder to store watermarks extracted from the modified images.
DCT-Watermark.ipynb       - The main script for the project, implementing the DCT-based watermarking algorithm.
input_image.jpg           - The input image that will have the watermark applied.
custom_watermark.jpg      - The custom image that will serve as the watermark.
watermarked_image.jpg     - The resulting image with the watermark applied.
README.md                 - This file, providing details and instructions for the project.
```


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

### 1. `arnold_transform(img, iterations)`
Applies the Arnold transformation to scramble the watermark image for additional security. The Arnold transformation shuffles the pixel positions of the watermark image based on a mathematical formula. This transformation is reversible, meaning the original watermark can be restored by applying the inverse transformation with the same number of iterations.

#### Parameters:
- **`img`**: The watermark image to be scrambled (as a NumPy array or PIL Image).
- **`iterations`**: The number of iterations to apply the transformation. More iterations result in a more scrambled image.

#### Functionality:
- Shuffles the pixel positions using the formula:
  - New row index: `(i + j) % n`
  - New column index: `(i + 2 * j) % m`
- Each iteration further scrambles the image.

#### Example:
```python
# Scramble a watermark image with 10 iterations
scrambled_image = arnold_transform(watermark_image, iterations=10)
```

### 2. `dct2(image)` and `idct2(image)`

Perform the Discrete Cosine Transform (DCT) and its inverse (IDCT) on image blocks. These functions allow operations in the frequency domain, which is essential for embedding and extracting the watermark.

#### Parameters:
- **`image`**: A 2D NumPy array representing an image or a block of an image.

#### Functionality:
- **`dct2(image)`**:
  - Converts the spatial domain of the image to the frequency domain.
  - Helps isolate the low- and high-frequency components of the image.
- **`idct2(image)`**:
  - Reconstructs the original image block from its frequency components.
  - Used to revert the modified DCT coefficients back into the spatial domain.

#### Example:
```python
# Compute the DCT and inverse DCT of an image block
dct_block = dct2(image_block)
restored_block = idct2(dct_block)
```

### 3. `embed_watermark(image, watermark, A, watermark_scale)`

Embeds the watermark into the image using DCT. This function modifies the frequency domain coefficients of the image to incorporate the watermark, ensuring it remains invisible to the human eye.

#### Parameters:
- **`image`**: The cover image into which the watermark will be embedded.
- **`watermark`**: The watermark image to be embedded.
- **`A`**: A scaling factor for adjusting the strength of the watermark in the frequency domain.
- **`watermark_scale`**: The scale factor for resizing the watermark to fit the cover image.

#### Functionality:
1. Converts both the cover image and the watermark to grayscale.
2. Resizes the watermark according to the `watermark_scale` parameter.
3. Applies the Arnold transformation to scramble the watermark.
4. Divides the cover image into 8×8 blocks and computes the DCT for each block.
5. Modifies the DCT coefficients of each block based on the scrambled watermark.
6. Performs the IDCT to reconstruct the watermarked image.

#### Example:
```python
# Embed a watermark into the cover image
watermarked_image = embed_watermark(cover_image, watermark, A=800, watermark_scale=2)
```
### 4. `extract_watermark(watermarked_image, original_image)`

Extracts the embedded watermark from the watermarked image. This function compares the DCT coefficients of the watermarked and original images to reconstruct the watermark.

#### Parameters:
- **`watermarked_image`**: The image containing the embedded watermark.
- **`original_image`**: The original image without the watermark.

#### Functionality:
1. Divides both the watermarked and original images into 8×8 blocks.
2. Computes the DCT of each block from both images.
3. Extracts watermark bits by analyzing the difference between specific DCT coefficients.
4. Reconstructs the binary watermark image.

#### Example:
```python
# Extract the watermark from the watermarked image
extracted_watermark = extract_watermark(watermarked_image, original_image)
```

### 5. `imageVSwatermark_accuracy(image_index, template, inverted_template)`

Evaluates the accuracy of the extracted watermark using template matching. This function compares the extracted watermark against the original and inverted watermark templates to determine the degree of similarity.

#### Parameters:
- **`image_index`**: The index of the image being evaluated (used for file handling).
- **`template`**: The original watermark template (as a NumPy array).
- **`inverted_template`**: The inverted version of the watermark template.

#### Functionality:
1. Loads the extracted watermark image and compares it to the `template` and `inverted_template` using OpenCV’s `matchTemplate` function.
2. Computes a similarity score (normalized correlation coefficient) for both templates.
3. Selects the highest score as the best match and evaluates the accuracy.

#### Example:
```python
# Evaluate the accuracy of the extracted watermark for image 1
template, inverted_template = imageVSwatermark_accuracy(1, template, inverted_template)
```

### Summary Table

| **Function**                 | **Purpose**                                                                    |
|------------------------------|--------------------------------------------------------------------------------|
| `arnold_transform`           | Scrambles the watermark image to add security.                                 |
| `dct2` and `idct2`           | Perform DCT and IDCT to work in the frequency domain.                          |
| `embed_watermark`            | Embeds the watermark into the cover image using DCT.                           |
| `extract_watermark`          | Extracts the watermark from the watermarked image.                             |
| `imageVSwatermark_accuracy`  | Evaluates the similarity between extracted and original watermarks using template matching. |

## Image Transformations

The project includes several transformations applied to the watermarked image to test the robustness of the watermark:

- **Histogram Equalization**
- **Gaussian Blur**
- **Mean Filtering**
- **Salt and Pepper Noise**
- **Bilateral Filtering**
- **Rotation**
- **Sharpening**
- **K-means Clustering Compression**
- **Wave Distortion**

Each transformation is applied, and the results are saved in the `modified_images` directory for further analysis.

## Conclusion
This project demonstrates the process of embedding an invisible digital watermark into an image using Discrete Cosine Transform (DCT). The watermark remains undetectable to the human eye but can be extracted after various image transformations. This technique provides a robust solution for protecting the copyright of digital images and ensuring the ownership of the content.

