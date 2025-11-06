---
layout: page
title: Multi-Parameter Physiological Monitoring System
description: Real-time monitoring of ECG, SpO2, respiration, temperature, and blood pressure with Qt/QML desktop and web interfaces
# img: assets/img/ecg-eeg.jpg
importance: 5
category: signal-processing
toc:
  sidebar: left
---

## Overview

Real-time 5-parameter physiological monitoring system (ECG, SpO2, respiration, temperature, blood pressure) with STM32 hardware and dual interface (Qt/QML desktop + HTML/JavaScript web). Achieves <50ms latency with Python+QML architecture for improved maintainability over traditional C++/XML.

## Problem Statement

Clinical monitoring requires simultaneous multi-parameter tracking with complex UIs and cross-platform deployment. Traditional C++/XML approaches are difficult to maintain and port across diverse medical hardware/OS environments.

## Methodology

### Hardware Architecture
- **STM32 Microcontroller**: 16-bit ADC, 100-1000 Hz sampling, 5-channel input (ECG 2-lead, SpO2, respiration, temperature, BP)
- **Signal Conditioning**: Analog filtering, amplification, impedance matching

### Software Architecture
- **Desktop**: Qt/QML frontend with Python backend, QtCharts real-time plotting
- **Web**: HTML/JavaScript with WebSocket streaming for remote access
- **Signal Processing**: Wavelet/FFT filtering, IIR filters (Butterworth/Chebyshev), QRS detection, HRV calculation

## Results

**Performance Metrics**:
- QRS detection accuracy: >98%
- Multi-signal display latency: <50ms
- Successful 5-parameter simultaneous acquisition
- Cross-platform validated (Windows, Linux)
- Multi-user web access functional

## Applications

- ICU patient monitoring (5-parameter tracking)
- Cardiac rehabilitation (ECG + SpO2)
- Respiratory assessment centers
- Ambulatory monitoring systems
- Research-grade signal acquisition

## Achievements & Recognition

### Key Metrics
- 5 physiological parameters monitored simultaneously
- <50ms real-time processing latency
- Dual interface deployment (desktop + web)
- Cross-platform compatibility (Windows, Linux, macOS)

### Technical Stack
Qt/QML, Python, HTML/JavaScript, WebSocket, STM32

## Timeline

**Duration**: February - July 2022 (6 months)
