---
layout: page
title: ECG & EEG Real-Time Signal Detection System
description: Multi-protocol physiological signal acquisition and visualization
img: assets/img/ecg-eeg.jpg
importance: 5
category: signal-processing
---

## Overview

A comprehensive real-time physiological signal acquisition and processing platform supporting both ECG and EEG monitoring with hardware integration, real-time filtering, and cross-platform visualization dashboards.

## Problem Statement

Clinical physiological monitoring faces several challenges:
- Need for multi-protocol hardware support (ECG, EEG, EMG)
- Real-time signal conditioning and artifact removal
- Low-latency visualization for immediate clinical feedback
- Cross-platform deployment for diverse clinical environments

## Key Achievements

- **Hardware Integration**: STM32 microcontroller-based acquisition module
- **Real-time Processing**: <50ms latency for clinical monitoring
- **Dual Dashboard**: Qt/QML for desktop + HTML/JavaScript for web-based visualization
- **Multi-modal Analysis**: Simultaneous ECG and EEG processing and display
- **Cross-platform Deployment**: Windows, Linux, macOS support

## Technology Stack

### Hardware Layer
- **STM32 Microcontroller**: Data acquisition and real-time preprocessing
- **ADC Configuration**: 16-bit resolution, configurable sampling rates (100-1000 Hz)
- **Signal Conditioning**: Analog filtering, amplification, impedance matching

### Signal Processing
- **Wavelet/FFT filtering**: Artifact removal and frequency domain analysis
- **Real-time IIR filters**: Butterworth, Chebyshev designs for ECG/EEG
- **Anomaly detection**: Automated QRS complex detection, spike identification
- **Peak analysis**: Automated R-peak detection, HRV calculation

### Visualization & Control
- **Qt/QML Dashboard**:
  - Real-time signal plotting
  - Parameter configuration
  - Data export and logging
  - Statistical summaries

- **Web Interface (HTML/JavaScript)**:
  - Browser-based monitoring
  - Remote access capability
  - Responsive design for mobile devices
  - WebSocket communication

## Results

- Successfully demonstrated simultaneous ECG (lead I, II) and EEG (4-channel) acquisition
- Clinical validation: QRS detection accuracy >98%
- Sub-50ms latency achieved with optimized buffer management
- Multi-user access via web interface validated

## Clinical Applications

- ICU patient monitoring
- Sleep study centers (EEG-specific)
- Cardiac rehabilitation facilities
- Ambulatory monitoring systems
- Research-grade signal acquisition

## Project Collaborators

**Key Laboratory of Non-Destructive Testing, Ministry of Education, China**

## Links

- **Code**: [GitHub - arnold117](https://github.com/arnold117)
- **Hardware Design**: Available upon request

## Timeline

- **Start**: February 2022
- **End**: July 2022
- **Duration**: 6 months
