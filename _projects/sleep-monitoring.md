---
layout: page
title: Android Sleep Quality Monitoring System
description: BEng thesis, 80% accurate sleep quality monitoring using phone sensors with volunteer validation
# img: assets/img/sleep-monitoring.jpg
importance: 6
category: signal-processing
toc:
  sidebar: left
---

## Overview

Android-based sleep quality monitoring system using built-in smartphone sensors (accelerometer, light sensor, microphone) without external devices. Achieves 80% agreement with commercial wearables across 20-volunteer validation, with demonstrable sleep quality improvement over 2-week monitoring.

## Problem Statement

Poor sleep quality affects cognitive function, increases chronic disease risk (diabetes, hypertension, depression), yet assessment relies on subjective questionnaires. Lab-based PSG is expensive and inaccessible; wearables have limited data access and proprietary formats. Need for objective, accessible, privacy-preserving daily monitoring.

## Methodology

### Sensor-Based Monitoring
- **Accelerometer**: Body movement tracking for sleep vs. awake detection, posture analysis
- **Light Sensor**: Environment adequacy assessment (target <10 lux), disruption monitoring
- **Microphone**: Noise level detection (target <32 dB), snoring identification, respiratory pattern analysis

### Sleep Quality Metrics
- Sleep duration, efficiency [(sleep time / time in bed) × 100%]
- Deep sleep ratio, breathing quality
- Environment quality (light + noise)
- Sleep stages: Awake, Light Sleep, Deep Sleep, Disruptions

### Implementation
- **Stack**: Kotlin, Android 8.0+ (API 26+), multi-threaded background service
- **Privacy**: All processing on-device, no cloud dependency

## Results

**Validation (20 volunteers, 1-week monitoring)**:
- 80% agreement with commercial wearables
- Sleep onset/offset timing: ±15-20 minutes difference (button press vs. sensor detection)
- Battery drain: 4-5% per 8-hour session, <3% CPU, <50 MB memory

**Sleep Quality Improvement**:
- Week 1: Poor quality despite adequate duration (stress-related irregular sleep, poor breathing)
- Week 2 (after behavioral recommendations): Improved deep sleep balance and breathing quality

## Applications

- Personal sleep quality tracking and optimization
- Sleep disorder screening (sleep apnea, insomnia)
- Circadian rhythm monitoring
- Mental health assessment (sleep-mood correlation)
- Academic/workplace performance optimization

## Limitations & Future Work

**Limitations**: Button-press manual markers (±15-20min error), single-site validation, university student cohort only

**Future Directions**:
- Automatic sleep onset/offset detection
- Multi-demographic validation
- Integration with wearable heart rate sensors

## Achievements & Recognition

### Key Metrics
- 80% accuracy vs. commercial wearables
- 20-volunteer validation with measurable QoL improvement
- <5% battery drain per night, on-device privacy

### Technical Stack
Kotlin, Android (multi-threading, background services), sensor fusion algorithms

## Team & Collaboration

**Supervisor**: Asst Prof. Yu Zulong (余祖龙)  
**Institution**: Department of Biomedical Engineering, Nanchang Hangkong University  
**Author**: Zhou Yanuo (BEng graduation thesis)

## Timeline

**Duration**: September 2022 - June 2023 (9 months, BEng thesis project)
