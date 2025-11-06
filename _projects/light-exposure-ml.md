---
layout: page
title: AI-Driven Light Exposure Classification
description: ML framework for circadian health phenotyping from wearable sensors
# img: assets/img/light-exposure.jpg
importance: 1
category: ai-health
toc:
  sidebar: left
---

## Overview

An MSc Capstone project developing a reproducible deep learning pipeline for classifying biologically relevant light exposure contexts from wearable spectral data. Current circadian health research relies on simplistic intensity thresholds that fail to capture meaningful differences in exposure contexts (natural vs. artificial light; indoor vs. outdoor). This work introduces a transparent, participant-wise generalized framework that prioritizes spectral shape over absolute intensity, enabling robust classification of light exposure contexts as potential digital biomarkers for circadian health monitoring. The system achieved 88.1% accuracy (AUC 0.938) in distinguishing natural from artificial light using ActLumus wearable spectroradiometer data from 26 participants.

## Problem Statement

**Research Gaps**: Threshold-based light exposure methods fail systematically—cloudy daylight (~200 lux) gets classified as "dim" despite broad-spectrum natural light, while bright indoor LED (~500 lux) gets misclassified as "outdoor" based on intensity alone. Iso-illuminant conditions (same lux, different spectra) produce divergent biological effects that current methods cannot distinguish.

**Three Critical Challenges**:
1. **Missing contextual differentiation**: Most studies emphasize intensity, neglecting spectral composition and temporal dynamics crucial for circadian regulation
2. **Data processing complexity**: Wearable devices produce noisy, imbalanced time-series with non-wear periods requiring robust preprocessing
3. **Lack of standardized workflows**: Open-source tools differ in implementation, yielding inconsistent results across studies

**Why This Matters**: Light regulates circadian physiology via intrinsically photosensitive retinal ganglion cells (ipRGCs) affecting melatonin secretion, hormone rhythms, metabolic processes, and cognitive performance. Natural daylight provides broad spectral composition (~400-800nm) with dynamic diurnal variation, while artificial sources exhibit narrower, temporally inconsistent spectra—driving distinct circadian responses even at identical lux levels.

## Methodology

**Dataset**: cyepi study (Tübingen, Germany, Aug-Nov 2023) with 26 participants wearing ActLumus spectroradiometers for 7 days, providing 10-second resolution across 10 spectral channels (F1-F8, IR, CLEAR). Ground truth from daily mHLEA questionnaires describing exposure context. Public dataset from Guidolin et al. (2024)—no new data collected.

**Pipeline Design Principles**:
- **Participant-wise generalization**: All train/validation/test splits preserve subject boundaries to prevent data leakage
- **Physical interpretability**: Feature engineering grounded in circadian photobiology
- **Reproducibility**: Configuration-driven with fixed random seeds and environment hashes

**Processing Sequence**:
1. **Domain Selection**: Raw sensor (10 channels) / α-opic projections (5 photoreceptor-weighted) / SPD reconstructions (12 bands)
2. **Logarithmic Transformation**: log₁₀(max(x, 10⁻⁴)) to stabilize dynamic range
3. **L2 Normalization**: Per-channel normalization prioritizing spectral shape over absolute intensity
4. **Hour-Medoid Aggregation**: Robust temporal summarization resistant to outliers and non-wear periods
5. **Cyclic Hour Encoding**: Sin/cos features to capture circadian priors without midnight discontinuities
6. **Model Training**: MLP with Bayesian hyperparameter optimization (288 configurations tested)

**Key Innovation**: L2 normalization with absolute intensity **excluded** prioritizes spectral shape, outperforming magnitude-based approaches. Raw sensor domain preserves broadband/NIR information, matching or exceeding α-opic projections.

## Results

**Primary Task (Natural vs. Artificial Light)**:
- **Test Performance**: AUC 0.938, Accuracy 88.1%, Precision 91.4%, Recall 88.7%
- **Generalization**: All Top-20 CV-selected configurations achieved test AUC > 0.93 across held-out participants
- **288-Configuration Grid Search**: Systematic evaluation showing robustness to preprocessing variations

**Feature Importance**:
- **Top predictors**: IR.LIGHT, CLEAR (broadband), cyclic hour features
- **Spectral patterns**: Mid-bands (550-630nm) differentiate artificial sources; short/long wavelengths elevate for natural light
- **Temporal priors**: Time-of-day does not act alone; spectral channels provide complementary discriminative power

**Exploratory Task (Indoor vs. Outdoor)**: Test AUC ~0.663, demonstrating that spectral data alone provide insufficient evidence without contextual sensors (GPS, accelerometry). Indoor daylight (window-filtered) mimics outdoor spectra, causing classification challenges.

**Negative Evidence** (transparent reporting): PCA aids interpretation but not required for optimal performance; SMOTE-Tomek underperforms under real-world priors compared to participant-wise evaluation without aggressive resampling.

## Applications

**Digital Biomarker Development**: Framework enables derivation of natural light dose profiles, light regularity indices (phase stability/variability), and exposure timing metrics as potential correlates for sleep quality, mood, and metabolic health outcomes.

**Clinical & mHealth**: Real-time exposure classification enables personalized light intervention adherence monitoring, dose quantification for circadian therapies, and integration into LightSPAN-style mobile health applications.

**Evidence-Based Policy**: Informs urban planning (outdoor space design), workplace lighting standards, and educational environment optimization based on quantified natural vs. artificial light exposure patterns.

**Sensor Optimization**: Identifies critical spectral channels (broadband, NIR) for cost-effective wearable device design, reducing hardware complexity while maintaining classification performance.

## Achievements & Recognition

**Academic Contribution**: First systematic application of deep learning to ActLumus wearable spectra for contextual light exposure classification, challenging intensity-centric assumptions in circadian research.

**Methodological Innovation**:
- Reproducible pipeline with transparent preprocessing and participant-wise generalization preventing data leakage
- Systematic comparison of raw sensor vs. α-opic vs. SPD domains, L2 normalization variants, and dimensionality reduction approaches
- Negative evidence reporting (PCA, SMOTE-Tomek limitations) to guide future research

**Publications**:
- **MSc Thesis** (expected submission Nov 2025): Zhou, Y. "AI-Driven Light Exposure Classification: A Reproducible Deep Learning Pipeline for Circadian Health Phenotyping from Wearable Spectral Data." *MSc Precision Health and Medicine, National University of Singapore*, 2025
- **Keywords**: Circadian Physiology, Light Exposure Classification, Wearable Sensors, Deep Learning, Digital Biomarkers, Reproducible Research

**Key Metrics**:
- 88.1% classification accuracy with 0.938 AUC
- 26 participants, 7-day recordings per subject
- 288 hyperparameter configurations evaluated
- 10-second temporal resolution spectral data

## Team & Collaboration

**Principal Supervisor**: Prof. Dr. Manuel Spitschan (Technical University of Munich, Head of LightSPAN Group, TUM-CREATE Principal Investigator)

**Institution**: TUM-CREATE (National Research Foundation Singapore, collaborating with Technical University of Munich, National University of Singapore, Nanyang Technological University)

**Data Source**: Guidolin et al. (2024) cyepi study public dataset (protocol approved by local ethics committee, data de-identified prior to release)

**Degree Program**: MSc Precision Health and Medicine, National University of Singapore

## Timeline

**Duration**: August 2024 - October 2025 (14 months)  
**Thesis Defense**: October 2025
