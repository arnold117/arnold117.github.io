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

Complete U-Net implementation for automatic skin lesion segmentation, from data annotation to PyQt5 GUI deployment. Achieves 0.759 mIoU (lesion 0.62, background 0.90) and 0.8708 mean pixel accuracy on 161 annotated dermatology images for objective lesion boundary detection.

## Problem Statement

Dermatological assessment relies on subjective visual inspection, causing inconsistent boundary detection, difficulty quantifying morphology changes, and high inter-observer variability. Automated segmentation provides objective, quantitative, and standardized lesion monitoring.

## Methodology

### Pipeline Architecture
1. **Data Annotation**: LabelMe tool for polygon-based lesion labeling (JSON → PNG masks), 161 annotated images
2. **Model Training**: U-Net (encoder-decoder with skip connections), batch size 16, 200 epochs, Dice + Cross-Entropy loss
3. **Validation**: mIoU, Precision, Recall, pixel accuracy metrics
4. **GUI Deployment**: PyQt5 interface for real-time segmentation visualization

### Technical Details
- **Dataset**: 161 annotated dermatology images (local dataset)
- **Stack**: PyTorch, torchvision, scikit-learn, PyQt5
- **Preprocessing**: FFT denoising + data augmentation for small-sample robustness
- **GPU Acceleration**: 50-100× faster than CPU training

## Results

**Segmentation Performance** (from confusion matrix):
- **Mean IoU**: 0.759
  - Lesion (nidus) IoU: 0.62
  - Background IoU: 0.90
- **Mean Pixel Accuracy**: 0.8708
- **Precision**: 0.844 mean (nidus 0.731, background 0.957)
- **Recall**: 0.871 mean (nidus 0.807, background 0.935)
- **Real-time inference** on 512×512 images

**Confusion Matrix Details**:
- Background: TP 639,513,107 | FP 29,028,863
- Nidus (lesion): TP 121,361,231 | FP 44,670,125

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
- **Mean IoU**: 0.759 (calculated from confusion matrix)
- **Class-specific IoU**: Lesion 0.62, Background 0.90
- **Mean Pixel Accuracy**: 0.8708
- **Mean Precision**: 0.844 | **Mean Recall**: 0.871
- **Dataset**: 161 annotated images (local dataset)
- End-to-end pipeline from annotation (LabelMe) to GUI deployment (PyQt5)
- GPU-accelerated real-time inference (50-100× speedup)

### References
- Ronneberger et al. (2015). "U-Net: Convolutional Networks for Biomedical Image Segmentation"
- LabelMe annotation tool (Wkentaro)

## Timeline

**Duration**: February - June 2021 (5 months)
