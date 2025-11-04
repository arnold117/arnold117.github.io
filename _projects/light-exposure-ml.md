---
title: "AI-Driven Light Exposure Classification"
date: 2024-10-15
featured: true
# thumb: /images/project-thumbs/light-exposure.jpg
summary: "Machine learning framework for classifying light exposure patterns from wearable spectral sensors. Achieved AUC≈0.93 using participant-wise cross-validation with α-opic metrics and spectral power distribution features."
tags: [digital-phenotyping, wearables, machine-learning, light-health]
links:
  - text: Code
    url: https://github.com/arnold117/light-exposure-ml
  - text: Poster
    url: /files/light_poster.pdf
  - text: Preprint
    url: https://arxiv.org/abs/TODO
---

## Overview

This project develops an AI-driven framework for classifying human light exposure patterns using data from wearable spectral sensors. Understanding light exposure is crucial for studying circadian rhythms, sleep quality, and overall health.

## Problem Statement

Traditional methods for assessing light exposure rely on simple lux measurements, which fail to capture the spectral composition of light that drives biological responses. We need more sophisticated approaches that:

- Account for the spectral power distribution (SPD) of light
- Incorporate α-opic metrics (melanopic, rhodopic, etc.)
- Handle inter-individual variability
- Work in real-world, free-living conditions

## Methodology

### Data Collection
- **Sensors:** Wearable spectroradiometers worn by participants
- **Duration:** 7-14 days of continuous monitoring
- **Features:** 36-channel spectral data (380-780nm), ambient temperature, accelerometry

### Feature Engineering
- Calculated 5 α-opic irradiance values (melanopic, rhodopic, chloropic, cyanopic, erythropic)
- Extracted spectral features (peak wavelength, spectral width, color temperature)
- Temporal features (time of day, day of week, season)
- Context features (indoor/outdoor likelihood, activity level)

### Model Architecture
- **Base Model:** Gradient Boosting (XGBoost)
- **Validation:** Participant-wise cross-validation to prevent data leakage
- **Ensemble:** Stacked model with Random Forest and Neural Network

## Results

- **Classification Accuracy:** 91.3% (5-class light exposure categories)
- **AUC-ROC:** 0.93 (weighted average)
- **Key Finding:** Melanopic irradiance + time-of-day features were the strongest predictors
- **Generalization:** Model maintained 87% accuracy on held-out participants

## Impact & Applications

This framework enables:
- Personalized light exposure recommendations for circadian health
- Large-scale epidemiological studies of light and health
- Real-time feedback systems for wearable devices
- Integration with smart home/office lighting systems

## Code & Resources

The full implementation is available on [GitHub](https://github.com/arnold117/light-exposure-ml) (TODO: update link). The repository includes:
- Data preprocessing pipelines
- Feature extraction modules
- Model training scripts
- Evaluation notebooks
- Documentation and examples

## Future Work

- Extend to predict subjective alertness and mood
- Integrate with sleep tracking data
- Develop real-time classification for wearable deployment
- Explore transfer learning across different sensor types

---

**Keywords:** Digital Phenotyping, Wearable Sensors, Light Exposure, Machine Learning, Circadian Health, α-opic Metrics
