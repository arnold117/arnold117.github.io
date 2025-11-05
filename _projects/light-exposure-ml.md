---
layout: page
title: AI-Driven Light Exposure Classification
description: ML framework for circadian health phenotyping from wearable sensors
img: assets/img/light-exposure.jpg
importance: 1
category: ai-health
---

## Overview

An MSc Capstone and TUM-CREATE research project developing an AI-driven framework for classifying human light exposure patterns using data from wearable spectral sensors. Understanding light exposure is crucial for studying circadian rhythms, sleep quality, and overall health.

## Key Achievements

- **AUC 0.93+**: Classification accuracy on light exposure patterns (5-class)
- **Config-driven Pipelines**: 288-configuration grid search for hyperparameter optimization
- **Circadian Timing Features**: Melanopic sensitivity and time-of-day as strongest predictors
- **Medoid Aggregation**: Robust model selection via unsupervised aggregation
- **Audit-ready Workflows**: Full reproducibility with seeded random states and frozen environments
- **Real-world Deployment**: Validated on free-living data from 50+ participants


## Motivation

Light exposure patterns drive circadian rhythms, sleep quality, and metabolic health. Traditional methods rely on simple lux measurements, which fail to capture spectral composition:

- **Melanopic Irradiance**: Measures circadian-relevant light (blue-enriched)
- **Spectral Power Distribution (SPD)**: Full spectrum characterization
- **Individual Variability**: Person-specific sensitivity to light
- **Real-world Conditions**: Free-living naturalistic data collection

## Technology Stack

### Data Collection & Preprocessing
- **Sensors**: Wearable spectroradiometers (36-channel spectral data, 380-780nm)
- **Duration**: 7-14 days continuous monitoring
- **Sampling**: 1-minute intervals with accelerometry and temperature
- **Preprocessing**: Interpolation, outlier removal, normalization

### Feature Engineering
- **α-opic Irradiance**: Melanopic, rhodopic, chloropic, cyanopic, erythropic
- **Spectral Features**: Peak wavelength, spectral width, color temperature
- **Temporal Features**: Hour of day, day of week, seasonal cycle
- **Context Features**: Indoor/outdoor likelihood, activity level
- **Log/L2 Normalization**: Robust scaling across participants

### Model Architecture
- **Base Model**: XGBoost (gradient boosting)
- **Validation Strategy**: Participant-wise 5-fold CV (prevent data leakage)
- **Ensemble**: Stacked XGBoost + Random Forest + Neural Network
- **Hyperparameter Grid**: 288 configurations (learning rate, depth, regularization)
- **Model Selection**: Medoid aggregation (most representative performer)

## Results

### Classification Performance
- **Accuracy**: 91.3% on 5-class light exposure categories
- **AUC-ROC**: 0.93 (weighted average across all classes)
- **Generalization**: 87% accuracy on held-out participants
- **Feature Importance**: Melanopic irradiance + time-of-day >> other features

### Light Exposure Categories
1. **Outdoor (high circadian-active light)**: >1000 melanopic lux
2. **Indoor bright (office/living room)**: 100-500 lux
3. **Indoor dim (evening/bedroom)**: 10-100 lux
4. **Darkness (nighttime)**: <10 lux
5. **Transition states**: Mixed lighting conditions

## Clinical Applications

- **Circadian Health Phenotyping**: Automated light exposure characterization
- **Sleep Quality Prediction**: Light patterns predict next-day sleep metrics
- **Personalized Recommendations**: Targeted light therapy advice
- **Population Studies**: Large-scale light and health epidemiology
- **Smart Systems Integration**: Real-time feedback for wearables/smart homes

## Supervisor

**Prof. Dr. Manuel Spitschan** - Technical University of Munich (TUM), Head of LightSPAN Group

## Links

- **Code**: [GitHub - arnold117](https://github.com/arnold117)
- **Supervisor**: [Prof. Dr. Manuel Spitschan](https://www.tum-create.edu.sg/)
- **Poster**: /files/light_poster.pdf

## Timeline

- **Start**: August 2024
- **End**: October 2025
- **Duration**: 14 months
- **Institution**: TUM-CREATE, National Research Foundation Singapore
