## Overview
![Architecture Diagram](./cnn.png)

The **Frequency Enhancement Network** is a deep learning framework designed to enhance cinematic film images by explicitly modeling different frequency components of an image.

Instead of processing the image as a single signal, the model separates it into **low-frequency (global structure), mid-frequency (contrast and shapes), and high-frequency (textures and edges)** components.  
Each frequency band is enhanced independently before being fused into a final high-quality output.

This approach improves texture sharpness, structural consistency, and perceptual realism compared to standard convolutional models.

---

## Methodology

### Baseline Model

A U-Net architecture was first implemented as a reference model.  
It learns a direct mapping from input image → enhanced image.

Loss function:

- **L1 Loss** → preserves pixel accuracy
- **SSIM Loss** → preserves perceptual structure

This baseline provides a measurable reference for improvement.

---

### Frequency Decomposition

The model uses a **Laplacian Pyramid Decomposition** to separate images into frequency bands:

- **Low Frequency** → global illumination and color tones
- **Mid Frequency** → structural information
- **High Frequency** → fine textures and edges

The decomposition ensures reconstruction error is near zero, validating correctness.

---

### Multi-Branch Frequency CNN

Each frequency band is processed using an independent convolutional branch:

- CNN_low → enhances global tone and lighting
- CNN_mid → improves structural consistency
- CNN_high → sharpens textures and fine details

The outputs are concatenated and fused using a **1×1 convolution layer**, allowing the network to learn optimal frequency recombination.

This architecture introduces explicit frequency awareness into the learning process.

---

### Training Strategy

The final objective combines:

- **Pixel Loss (L1)** → ensures numerical fidelity
- **Frequency Loss** → enforces consistency across decomposed bands
- **Perceptual Loss (VGG-based)** → improves visual realism

This multi-level supervision encourages both low-level accuracy and high-level perceptual quality.

---

### Evaluation Metrics

Model performance is evaluated using:

- **PSNR (Peak Signal-to-Noise Ratio)** → overall reconstruction fidelity
- **SSIM (Structural Similarity Index)** → structural preservation
- Visual comparison of texture regions and frequency maps

The multi-frequency model demonstrates improved texture sharpness and structural detail compared to the baseline U-Net.

---

## Key Contributions

- Explicit frequency-aware CNN architecture
- Laplacian pyramid integration inside deep learning pipeline
- Multi-branch design for specialized frequency enhancement
- Combined pixel + perceptual + frequency-domain supervision

---

## Applications

- Cinematic color grading
- Film-style image restoration
- Detail enhancement in photography
- Texture-aware image refinement

---

## Future Work

- Frequency attention mechanism
- GAN-based realism enhancement
- Style embedding for multiple cinematic profiles
- Higher resolution training (patch-based 512×512)

---

This project demonstrates a research-oriented approach to image enhancement by integrating classical signal processing concepts with modern deep learning architectures.
