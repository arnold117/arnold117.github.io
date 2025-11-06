---
layout: page
title: U-Net for Skin Lesion Segmentation
description: Complete implementation with LabelMe annotation, model training, validation, and PyQt5 GUI
# img: assets/img/dermatology.jpg
importance: 7
category: ai-health
toc:
  sidebar: left
---

## Overview

Complete U-Net implementation for automatic skin lesion segmentation, from data annotation to PyQt5 GUI deployment. Achieves 0.87 mIoU and 0.92 Dice coefficient for objective lesion boundary detection in dermatological images.

## Problem Statement

Dermatological assessment relies on subjective visual inspection, causing inconsistent boundary detection, difficulty quantifying morphology changes, and high inter-observer variability. Automated segmentation provides objective, quantitative, and standardized lesion monitoring.

## Methodology

### Pipeline Architecture
1. **Data Annotation**: LabelMe tool for polygon-based lesion labeling (JSON → PNG masks)
2. **Model Training**: U-Net (encoder-decoder with skip connections), batch size 16, 200 epochs, Dice + Cross-Entropy loss
3. **Validation**: mIoU, Precision, Recall, Dice coefficient metrics
4. **GUI Deployment**: PyQt5 interface for real-time segmentation visualization

### Technical Details
- **Stack**: PyTorch, torchvision, scikit-learn, PyQt5
- **Data Augmentation**: Multiple strategies for small-sample robustness
- **GPU Acceleration**: 50-100x faster than CPU training

## Results

**Segmentation Performance**:
- mIoU: 0.87 ± 0.05 | Dice: 0.92 ± 0.03
- Sensitivity: 0.89 | Specificity: 0.95
- Boundary accuracy: 2-3 pixels median error
- Real-time inference on 512×512 images

## Applications

- Melanoma screening support systems
- Treatment response monitoring
- Surgical planning and margin definition
- Population-level skin disease epidemiology

## Limitations & Future Work

- Multi-class segmentation (lesion type classification)
- 3D reconstruction from multiple views
- Clinical trial deployment and validation

## Achievements & Recognition

### Key Metrics
- 0.87 mIoU, 0.92 Dice coefficient
- End-to-end pipeline from annotation to GUI deployment
- GPU-accelerated real-time inference

### References
- Ronneberger et al. (2015). "U-Net: Convolutional Networks for Biomedical Image Segmentation"
- LabelMe annotation tool (Wkentaro)

## Timeline

**Duration**: February - June 2021 (5 months)
