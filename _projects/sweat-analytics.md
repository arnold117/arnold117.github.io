---
layout: page
title: Wearable Optical Sweat Analytics
description: Microfluidics and RGB colorimetry for biomarker detection
# img: assets/img/sweat-analytics.jpg
importance: 4
category: wearable-sensing
toc:
  sidebar: left
---

## Overview

Personalized wearable system for non-invasive sweat biomarker monitoring, combining Tesla valve microfluidics, RGB colorimetry, and AI analysis (~90% accuracy). Enables real-time detection of pH, glucose, lactate, cortisol, and electrolytes for health assessment.

## Problem Statement

Traditional blood/urine tests are invasive, require 24-72 hour lab turnaround, and lack continuous monitoring capability. No commercial wearable exists for real-time multi-biomarker sweat analysis despite strong clinical demand (cystic fibrosis, diabetes, stress monitoring).

## Methodology

### Hardware Design
- **Tesla Valve Microfluidics**: Passive one-way flow control without pumps, reduces contamination
- **RGB Photoelectric Colorimetry**: 100× cheaper than spectrometers, captures biomarker-reagent color changes
- **Wireless Transmission**: Bluetooth/Wi-Fi streaming to smartphone/PC

### AI Analysis Pipeline
1. RGB signal acquisition from test strips
2. Color space transformation (HSV/Lab normalization)
3. Neural network inference (3-layer fully connected, dropout regularization)
4. Personalized baseline calibration for user-specific accuracy

**Biomarkers Detected**: pH, glucose, lactate, cortisol, electrolytes (Na⁺, K⁺, Cl⁻)

## Results

**Performance**:
- Detection accuracy: ~90% agreement with laboratory methods
- Response time: <5 minutes (sweat contact to readout)
- Detection ranges: pH 4-8, glucose 0-200 mg/dL, lactate 5-50 mM
- Reproducibility: Inter-device CV <8%, intra-device CV <5%
- Wearability: 20+ hours continuous operation tested

## Applications

- Cystic fibrosis screening (elevated sweat chloride)
- Diabetes monitoring (non-invasive glucose tracking)
- Athletic performance optimization (hydration, lactate)
- Stress assessment (cortisol monitoring)
- Stroke rehabilitation (autonomic function mapping)

## Achievements & Recognition

### Awards
- **3rd Prize** - 10th National Student Optoelectronic Design Competition (2022)
- **NCHU 'Three Small Projects' Award**
- **National Innovation Project** - Completed with prototype

### Publications
**Talanta** (Q1 journal, IF ~6.0) - peer-reviewed publication on sweat biomarker detection

### Key Metrics
- ~90% detection accuracy
- ~$50 device cost (vs. >$5,000 lab equipment)
- ~$0.50 test strip cost (vs. $20-100 lab analysis)

## Team & Collaboration

**Principal Investigators**: A/Prof. Shi Huanhuan (石环环), Prof. Zhang Weiwei (张巍巍)  
**Institution**: Department of Biomedical Engineering, Nanchang Hangkong University  
**Core Contributors**: Zhou Yanuo (system integration, AI development), Xie Zhihao (circuit design), Cao Yu (data analysis, Talanta co-author)  
**Collaborators**: Nie Daosheng, Xin Jiliang, Yan Yuwei, Liu Yujie  
**Funding**: Outstanding Young Scientist Project (20192BCB23011)

## Timeline

**Duration**: September 2020 - July 2022 (22 months)  
**Competition**: October 2022
