---
layout: page
title: Multimodal Depression Detection via Smartphone Sensing
description: Machine learning biomarker discovery for depression using passive smartphone sensor data
# img: assets/img/depression-detection.jpg
importance: 2
category: ai-health
toc:
  sidebar: left
---

## Overview

Research-stage machine learning pipeline to identify behavioral indicators of depression using multimodal smartphone sensor data from 46 college students in the StudentLife dataset. Combines passive sensing (GPS, app usage, communication logs, physical activity) with data science to discover digital biomarkers for mental health.

## Problem Statement

Depression detection traditionally relies on subjective self-reporting and clinical interviews, which can be inconsistent and delay diagnosis. Passive smartphone sensing offers potential for continuous, objective monitoring of behavioral patterns associated with depression, enabling early intervention and longitudinal tracking.

## Methodology

### Dataset & Feature Engineering

**StudentLife Dataset**: 46 college students monitored for 10 weeks
**Modalities**: GPS location, app usage, communication patterns, physical activity
**Features**: 50 behavioral features extracted across four modalities

**Feature Categories**:
- **Location patterns**: GPS diversity, stationary time, location entropy
- **App usage**: Diversity variability, session frequency, usage patterns
- **Communication**: Call/SMS frequency, social interaction metrics
- **Physical activity**: Step counts, movement patterns, sedentary behavior

### Data Quality & Preprocessing

**Critical Discovery**: Identified and corrected label leakage that initially produced artificially perfect model accuracy
**Class Imbalance Handling**: Severe imbalance (4 positive vs. 42 negative cases)
- Balanced class weights implementation
- Stratified 5-fold cross-validation
- Careful evaluation metric selection (AUC-ROC over raw accuracy)

### Model Development

**ML Frameworks**: Scikit-learn (baseline models), PyTorch (deep learning)
**Model Types**:
- Traditional: Logistic Regression, Random Forest, XGBoost
- Deep Learning: Variational Autoencoders (VAE), Graph Neural Networks, Transformers
- Hardware: Apple Silicon MPS acceleration for neural networks

## Results

**Best Performance**: Logistic Regression achieved 76.2% AUC-ROC

**Top Biomarker**: App usage diversity variability
- **Clinical Interpretation**: Reflects anhedonia (loss of interest in activities)
- **Supporting Features**: Social withdrawal patterns, disrupted daily routines

**Model Insights**:
- Simplicity outperformed complexity in low-sample regime
- Feature interpretability crucial for clinical translation
- Behavioral variability more predictive than absolute values

## Applications & Clinical Context

**Research Applications**:
- Digital biomarker discovery for depression screening
- Longitudinal mental health monitoring
- Behavioral pattern analysis for early intervention
- Complement to traditional clinical assessment

**CRITICAL LIMITATIONS - NOT CLINICAL READY**:
- Sensitivity: Only 25% (misses 75% of positive cases)
- Sample size: n=46 insufficient for clinical deployment
- Generalizability: Limited to college-age population
- Validation: Lacks external clinical validation

## Limitations & Future Work

**Current Limitations**:
- Small sample size prevents robust generalization
- Single-population study (college students only)
- Privacy concerns with continuous sensing
- Battery and data usage considerations
- Temporal dynamics not fully captured

**Future Directions**:
- Multi-site validation studies with larger cohorts
- Integration with clinical assessments (PHQ-9, DASS-21)
- Privacy-preserving federated learning approaches
- Temporal modeling with LSTM/Transformer architectures
- Multi-task learning for depression severity prediction

## Achievements & Recognition

### Key Metrics
- 50 behavioral features engineered from multimodal sensor data
- 76.2% AUC-ROC with interpretable biomarkers
- Successfully identified and corrected data leakage issues
- Complete research pipeline: data processing → feature engineering → model training → clinical interpretation

### Technical Stack
Python, scikit-learn, PyTorch, pandas, NumPy, matplotlib, seaborn

### GitHub Repository
[multimodal-depression-detection](https://github.com/arnold117/multimodal-depression-detection)

## Ethical Considerations

**Data Privacy**: All data anonymized; passive sensing raises consent and surveillance concerns
**Clinical Safety**: Emphasized research-stage nature; not a diagnostic tool
**Bias Awareness**: Limited demographic diversity acknowledged in interpretation

## Timeline

**Duration**: November 2025 - December 2025 (Independent research project)
