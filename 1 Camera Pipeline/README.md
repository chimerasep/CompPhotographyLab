# BBM 444 - Programming Assignment 1: Camera Pipeline

## Overview

This project implements a basic image processing pipeline for developing RAW images captured using a DSLR camera (Nikon D40). The goal is to convert a RAW `.nef` file into a display-ready image through several steps of processing using Python and external tools like `dcraw`.

## Requirements

- Python 3.x  
- numpy >= 1.19.1  
- scipy >= 1.5.0  
- skimage >= 0.16.2  
- matplotlib >= 3.3.1  
- dcraw (v9.28 or newer)

## Pipeline Steps

1. **RAW to TIFF Conversion**:  
   Convert the RAW image (`.nef`) to `.tiff` using `dcraw -4 -D -T`.

2. **Initial Processing**:  
   - Load TIFF image using `skimage.io.imread`.
   - Convert to `float64` and normalize using black/white levels from `dcraw`.

3. **Bayer Pattern Detection**:  
   - Identify the Bayer pattern (`grbg`, `rggb`, etc.) for demosaicing.

4. **White Balancing**:  
   Implemented three approaches:
   - White World
   - Gray World
   - Camera multipliers from `dcraw`

5. **Demosaicing**:  
   Applied bilinear interpolation using `scipy.interpolate.RegularGridInterpolator`.

6. **Color Space Correction**:  
   Transformed from camera RGB to linear sRGB using the inverse of `MsRGB→cam`.

7. **Brightness & Gamma Correction**:  
   Adjusted mean grayscale intensity and applied gamma encoding per sRGB standard.

8. **Image Saving**:  
   - Saved output in `.png` and `.jpeg` (quality 95) using `skimage.io.imsave`.

## Manual White Balancing

Used user-selected white patches from the image with `matplotlib.pyplot.ginput()` to perform manual white balancing.

## dcraw Comparison

Used full auto-processing flags in `dcraw` to generate a reference image:
```
dcraw -w -T campus.nef
```
Compared with:
- Python-developed image
- dcraw result
- Camera-generated JPEG (sample.jpg)

## Files to Submit

- `notebook.ipynb` – code and report
- `campus.tiff` – converted linear RAW image
- `output.png`, `output.jpeg` – final results
- `dcraw_result.png` – auto-processed image
- Any figures used in markdown
- All within a ZIP named `name-surname(s)-assgn1.zip`

## Notes

- All functions are modularized and well-documented.
- Output is reproducible by rerunning the notebook.
- Figures are embedded in markdown cells for explanation.

---

Hacettepe University  
BBM 444 – Spring 2025