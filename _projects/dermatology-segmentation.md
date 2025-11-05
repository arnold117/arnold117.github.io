---
layout: page
title: U-Net Segmentation for Dermatology Images
description: Deep learning for medical image segmentation
img: assets/img/dermatology.jpg
importance: 7
category: ai-health
---

## Overview

A computer vision project implementing U-Net architecture for automated lesion segmentation in dermatological images, with focus on handling small-sample datasets common in medical imaging.

## Clinical Significance

Dermatological image segmentation enables:
- Automated lesion boundary detection
- Size and morphology quantification
- Follow-up comparison and monitoring
- Melanoma risk assessment
- Objective treatment response evaluation

## Key Achievements

- **Small-Sample Optimization**: High performance with <500 labeled images
- **Class-Specific IoU Breakdown**: Separate performance metrics for skin, lesion, background
- **Data Augmentation**: Custom strategies for medical image domain
- **Generalization**: Cross-validation on diverse skin types and lesion morphologies

## Methodology

### Dataset Preparation
- **Source**: Public dermatology image datasets (ISIC Archive)
- **Preprocessing**: 
  - Standardization to 512×512 resolution
  - Histogram equalization for consistency
  - Manual annotation verification
- **Size**: 450 training, 100 validation, 100 test images

### Data Augmentation Strategy
- **Geometric Transformations**: Rotation (0-90°), flipping, elastic deformation
- **Intensity Modifications**: Brightness/contrast adjustment, Gaussian blur
- **Domain Shifts**: Color space variations, synthetic shadow/lighting changes
- **Mixup**: Blending augmented samples for improved robustness

### Model Architecture

```
Input: 512×512 RGB Image
  ↓
Encoder: 4-level downsampling (64 → 512 filters)
  ↓
Bottleneck: Convolutional blocks
  ↓
Decoder: 4-level upsampling with skip connections
  ↓
Output: 512×512 binary segmentation mask
```

### Training Configuration
- **Optimizer**: Adam (learning rate 0.001)
- **Loss**: Dice Loss + Cross-Entropy (weighted combination)
- **Batch Size**: 16
- **Epochs**: 200 with early stopping
- **Validation**: 5-fold cross-validation

## Results

### Segmentation Performance
- **Mean IoU**: 0.87 ± 0.05
- **Dice Coefficient**: 0.92 ± 0.03
- **Sensitivity**: 0.89 (lesion detection)
- **Specificity**: 0.95 (false positive suppression)

### Class-Specific Metrics
- **Skin (Background)**: IoU = 0.94
- **Lesion**: IoU = 0.87
- **Boundary Accuracy**: 2-3 pixels median error

## Clinical Applications

- Melanoma screening support systems
- Treatment response monitoring (chemotherapy, immunotherapy)
- Surgical planning and margin definition
- Population-level skin disease epidemiology

## Future Work

- Multi-class segmentation (lesion type classification)
- 3D reconstruction from multiple views
- Integration with dermoscopy features
- Clinical trial deployment

## Links

- **Code**: [GitHub - arnold117](https://github.com/arnold117)
- **Dataset**: [ISIC Archive](https://www.isic-archive.com)

## Timeline

- **Start**: February 2021
- **End**: June 2021
- **Duration**: 5 months
