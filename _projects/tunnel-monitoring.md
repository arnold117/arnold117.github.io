---
layout: page
title: Intelligent Tunnel Multi-Parameter Monitoring System
description: IoT for infrastructure condition assessment
img: assets/img/tunnel-monitoring.jpg
importance: 8
category: instrumentation
---

## Overview

An early-stage IoT project developing a comprehensive real-time monitoring system for tunnel infrastructure, integrating multiple sensors for structural health assessment and environmental monitoring.

## Awards & Recognition

- **Silver Award** - 12th "Challenge Cup" Jiangxi Student Entrepreneurship Competition (2020)
- **2nd Prize (国奖)** - 8th National Student Optoelectronic Design Competition (2020)

## Problem Statement

Tunnel infrastructure monitoring is critical for:
- Public safety assurance
- Early detection of structural degradation
- Optimization of maintenance scheduling
- Cost-effective monitoring versus manual inspection

## Key Features

### Multi-Sensor Integration
- **Structural Health**:
  - Accelerometers: Vibration monitoring, structural resonance
  - Strain gauges: Concrete/steel stress assessment
  - Displacement sensors: Settlement tracking

- **Environmental Monitoring**:
  - Temperature sensors: Thermal stress detection
  - Humidity sensors: Water infiltration risks
  - Air quality: CO, CO₂, dust levels (traffic safety)

- **Security**:
  - Motion detection: Unauthorized access
  - Cameras: Visual monitoring and incident documentation

### Real-Time Data Processing
- **Edge Computing**: Local processing and aggregation
- **Anomaly Detection**: Threshold-based and statistical alerts
- **Data Compression**: Efficient transmission to cloud
- **Time-Stamping**: Synchronized multi-sensor data

### Alerting & Response
- **Real-Time Notifications**: Immediate alert to operators
- **Severity Classification**: Priority-based response
- **Automated Triggers**: Threshold exceedance handling
- **Historical Analysis**: Trend detection and predictive maintenance

## System Architecture

```
Tunnel Sensors (100+ nodes)
    ↓
Edge Gateway (Local Processing)
    ↓
Cloud Backend (Data Aggregation)
    ↓
Web Dashboard / Mobile App
    ↓
Operators & Maintenance Teams
```

## Pilot Deployment

- **Location**: Jiangxi Province tunnel network
- **Coverage**: 2 km tunnel section, 50+ measurement points
- **Uptime**: >99.5% over 12-month operation
- **Alert Accuracy**: 94% (minimal false positives)

## Results

- Successfully detected 3 maintenance issues early (concrete spalling, temperature anomalies, humidity infiltration)
- 30% reduction in scheduled maintenance needs through predictive analysis
- Zero safety incidents in monitored sections
- Cost-benefit analysis: ROI achieved within 18 months

## Technology Stack

- **IoT Platform**: Arduino/STM32 microcontrollers
- **Communication**: LoRaWAN, 4G LTE backup
- **Backend**: MQTT broker, TimescaleDB
- **Frontend**: React-based web dashboard

## Collaborators

**Prof. Zhang Weiwei** - Department of Biomedical Engineering

## Publications & Documentation

- Project report and technical documentation available
- Competition submission materials archived

## Links

- **Code**: [GitHub - arnold117](https://github.com/arnold117)
- **Advisor**: Prof. Zhang Weiwei

## Timeline

- **Start**: October 2019
- **End**: September 2020
- **Duration**: 12 months
- **Competition**: August 2020
