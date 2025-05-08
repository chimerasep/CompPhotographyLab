# BBM 446 - Programming Assignment 2: HDR Imaging and Tonemapping

## Overview

This project explores High Dynamic Range (HDR) imaging by combining multiple exposures of the same scene to produce a single HDR image. The assignment also covers radiometric calibration, color correction using a color checker, and photographic tonemapping for displaying HDR results.

## Requirements

- Python 3.x  
- numpy  
- skimage  
- matplotlib  
- cv2 (OpenCV)  
- dcraw  
- Provided `cp_assgn2.py` helper file

## Key Tasks

1. **HDR Imaging (60 pts)**  
   - Convert RAW images (.NEF) to linear TIFF using `dcraw` with high-quality demosaicing and white balance.
   - Linearize rendered (.JPG) images via radiometric calibration using Debevec & Malik's method.
   - Merge linear images into HDR using both linear and logarithmic methods.
   - Implement 4 weighting schemes: Uniform, Tent, Gaussian, and Photon.
   - Create 16 HDR images in total and pick the best one visually.

2. **Color Correction & White Balancing (20 pts)**  
   - Use color checker in the image to compute an affine color correction matrix.
   - Perform manual white balancing using patch 4.
   - Compare before and after correction visually.

3. **Photographic Tonemapping (20 pts)**  
   - Apply Reinhard’s tonemapping operator both in RGB and luminance (Y) space.
   - Tune brightness (K) and burn (B) parameters.
   - Gamma encode and display results.

4. **Bonus - Your Own HDR Images (50 pts)**  
   - Capture your own exposure stacks in RAW and JPG formats.
   - Apply same pipeline and tonemapping.
   - Submit HDRs and select best looking output.

## File Outputs

- Jupyter Notebook with source code and explanations
- Selected HDR images from each part
- Tonemapped visualizations (PNG, JPG)
- Figures used in report
- File: `name-surname(s)-assgn2.zip`

## Notes

- Work on downsampled images during development.
- Be cautious of memory usage.
- Always apply gamma encoding before displaying.
- Use `writeHDR` and `readHDR` to save/load HDRs.
- Use `gphoto2` to capture RAW+JPEG pairs for bonus.

---
