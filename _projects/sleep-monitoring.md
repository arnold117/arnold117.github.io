---
layout: page
title: Android Sleep Quality Monitoring System
description: Smartphone-based sleep monitoring without external devices
img: assets/img/sleep-monitoring.jpg
importance: 6
category: signal-processing
---

## Overview

A BEng graduation project developing an Android-based sleep quality monitoring system that leverages built-in smartphone sensors (accelerometer, light, microphone) to detect and classify sleep patterns without requiring external devices.

## Motivation

Sleep quality assessment is critical for health monitoring, but current solutions have limitations:
- Wearable devices require additional hardware investment
- Actigraphy studies rely on specialized equipment
- Smartphone ubiquity offers opportunity for scalable assessment
- Multi-sensor fusion can improve reliability and generalization

## Key Achievements

- **Comparable Performance**: Detection accuracy matching commercial wearable devices
- **Minimal Resource Overhead**: Battery drain <5% per night
- **Unexpected User Benefit**: Study participants reported improved sleep quality during monitoring period
- **Volunteer Validation**: Cross-validated with polysomnography ground truth on 30+ participants
- **Privacy-Preserving**: All processing on-device, no cloud transmission

## Technology Stack

### Mobile Platform
- **Language**: Kotlin
- **Target**: Android 8.0+ (API level 26+)
- **Architecture**: Multi-threaded background service with UI layer separation

### Sensor Integration
- **3-Axis Accelerometer**: Movement detection and posture classification
- **Ambient Light Sensor**: Sleep/wake cycle estimation, eye closure detection
- **Microphone**: Breath rate estimation, snoring detection, sleep talk recognition

### Data Processing Pipeline
1. **Raw Signal Collection**: 100 Hz sampling rate per sensor
2. **Feature Engineering**:
   - Accelerometer: Movement intensity, periodicity, posture changes
   - Light: Illuminance levels, temporal stability, on/off patterns
   - Audio: Spectral content, frequency bands, threshold-crossing events
3. **Multi-Sensor Fusion**: Weighted combination of sensor features
4. **Classification**: Random Forest + SVM ensemble for sleep vs. awake states
5. **Post-Processing**: Temporal smoothing, artifact removal

## Results

### Performance Metrics
- **Sleep Detection Sensitivity**: 92-95%
- **False Alarm Rate**: <5%
- **Latency**: Real-time processing with <2s classification window
- **Agreement with Wearables**: Kappa = 0.87

### Practical Findings
- Multi-sensor fusion outperformed single-sensor approaches
- Accelerometer most important for stage detection
- Light sensor critical for free-living validation
- Microphone provides valuable contextual information

## Clinical Applications

- Personal sleep tracking and trends
- Sleep disorder screening
- Sleep hygiene coaching
- Population-level sleep epidemiology studies

## Future Directions

- Extension to sleep stage classification (N1, N2, N3, REM)
- Integration with smart home systems
- Predictive alerting for sleep fragmentation
- Cross-platform deployment (iOS)

## Links

- **Code**: [GitHub - arnold117](https://github.com/arnold117)
- **Thesis**: Available upon request

## Timeline

- **Start**: September 2022
- **End**: June 2023
- **Duration**: 9 months
- **Defense**: June 2023
