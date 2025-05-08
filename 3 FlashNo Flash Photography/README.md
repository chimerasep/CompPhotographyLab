# BBM 444 - Programming Assignment 3: Flash/No-Flash Photography

## Overview

This project focuses on combining flash and no-flash image pairs to enhance image quality. The assignment covers bilateral and joint-bilateral filtering, flash-to-ambient detail transfer, shadow/specularity masking, and gradient-domain image fusion via Poisson reconstruction.

## Requirements

- Python 3.x  
- numpy  
- scipy  
- matplotlib  
- OpenCV (cv2)

## Key Tasks

### 1. Bilateral Filtering (100 pts)

- **Basic Bilateral Filter**: Denoising the ambient image.
- **Joint Bilateral Filter**: Use the flash image as guidance.
- **Detail Transfer**: Combine flash and filtered images to enhance details.
- **Shadow/Specularity Masking**: Mask harsh flash effects and blend results.

📌 Key equations:
- A<sub>Detail</sub> = A<sub>NR</sub> · F / (F<sub>Base</sub> + ε)
- A<sub>Final</sub> = (1 − M) · A<sub>Detail</sub> + M · A<sub>Base</sub>

### 2. Gradient-Domain Processing (100 pts)

- **Gradient Calculation**: Get ∇a, ∇Φ′ for ambient and flash.
- **Fused Gradient Field**: Use orientation coherence and saturation weighting to merge gradients.
- **Poisson Solver**: Use conjugate gradient descent to reconstruct image from gradients.
- **Parameter Tuning**: Experiment with σ, τ<sub>s</sub>, boundary conditions, and initialization.

### 3. Capture Your Own Image Pairs (100 pts)

- Capture one scene for bilateral denoising and another for gradient-domain fusion.
- Apply the full pipeline from above to produce your best image enhancements.

## File Outputs

- `assignment3.ipynb`: Code and markdown explanations
- `output/`: Processed and fused image results
- `data/`: Captured flash/no-flash image pairs
- ZIP named `b<studentID>.zip` containing all deliverables

## Notes

- Normalize images to [0,1] before filtering
- Gamma-correct nonlinear images with inverse sRGB gamma function
- Show difference images and compare methods
- Apply filters per color channel; use luminance for masking
- Use Poisson CGD solver for reconstruction
- Test: `div(grad(I)) ≈ Laplacian(I)` (excluding boundaries)

---

Hacettepe University  
BBM 444 – Spring 2025