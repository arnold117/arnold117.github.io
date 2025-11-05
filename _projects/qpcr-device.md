---
layout: page
title: Thermal Cycling Device for Fluorescence Quantitative PCR Instrument
description: Instrumentation design for PCR thermocycling
img: assets/img/qpcr.jpg
importance: 10
category: instrumentation
---

## Overview

A research and design project developing a precision thermal cycling system for fluorescence quantitative PCR (qPCR) instrumentation, with focus on temperature uniformity, rapid cycling speed, and optical integration.

## Recognition

**Successful Participant** - 2021 National Undergraduate Biomedical Engineering Innovation Design Competition

## Problem Statement

Thermal cycling is critical for qPCR success:
- **Temperature Uniformity**: ±0.5°C across sample block required
- **Ramp Rate**: Fast ramp speeds reduce cycling time while maintaining accuracy
- **Reproducibility**: Cycle-to-cycle consistency essential for quantification
- **Optical Integration**: Compatibility with fluorescence detection optics

## Technical Objectives

1. Design precision temperature controller
2. Achieve rapid ramping (>2°C/second)
3. Maintain ±0.5°C uniformity across 96-well plate
4. Integrate optical path for fluorescence readout
5. Minimize power consumption and heat dissipation

## System Design

### Thermal Control
- **Heat Source**: Peltier elements (TEC modules) for precise heating/cooling
- **Temperature Sensor**: RTD (Pt100) in control loop feedback
- **Block Material**: Aluminum for optimal thermal conductivity
- **Insulation**: Foam + reflective barriers for efficiency

### Controller Electronics
- **Microcontroller**: STM32 ARM-based processor
- **PID Loop**: Tuned for fast response, minimal overshoot
- **DAC Output**: 0-5V control signals to TEC driver circuits
- **Monitoring**: Real-time temperature logging and diagnostics

### Thermal Profiling
- **Denaturation**: 94-95°C (30 seconds)
- **Annealing**: 55-65°C (30 seconds, variable)
- **Extension**: 72°C (30-60 seconds)
- **Cool-down**: 4°C (holding)

## Performance Specifications

### Temperature Performance
- **Uniformity**: ±0.3°C across 96 wells
- **Ramp Rate**: 2.5°C/second heating, 2.0°C/second cooling
- **Overshoot**: <0.2°C beyond setpoint
- **Stability**: ±0.1°C drift over 30-cycle run

### Cycle Performance
- **Cycle Time**: 45-60 seconds (3-step cycling)
- **Total Runtime**: <2 hours for 40 cycles
- **Repeatability**: Cycle CV < 2%

## Optical Integration

- **Excitation Path**: LED or laser excitation at 480-530nm
- **Emission Path**: Optical filter at 510-550nm
- **Detector**: Photodiode or CCD camera array
- **Calibration**: Reference dye standards for quantification

## Experimental Validation

### Thermal Characterization
- K-type thermocouple validation across sample block
- Temperature stability over 40-cycle run
- Ramp rate verification with multiple profiles

### qPCR Validation
- Standard curve generation (R² > 0.99)
- Copy number detection across 6 orders of magnitude
- Reproducibility testing with replicate samples
- Comparison to commercial instruments

## Manufacturing Considerations

- **Scale-Up**: Transfer design to production engineering
- **Cost Target**: <$2000 per unit
- **Reliability**: MTBF > 10,000 hours
- **Safety**: Thermal overload protection, circuit redundancy

## Applications

- Research-grade qPCR systems
- Diagnostic PCR platforms
- Education and training instruments
- Portable/benchtop qPCR devices

## Collaborators & Supervisors

**Key Laboratory of Non-Destructive Testing, Ministry of Education, China**

## Future Enhancements

- Gradient temperature cycling for optimization
- Multi-channel optical detection
- Integration with microfluidic cartridges
- Smart thermal profiling AI optimization

## Links

- **GitHub**: [arnold117](https://github.com/arnold117)
- **Documentation**: Technical specifications available upon request

## Timeline

- **Start**: February 2021
- **End**: June 2021
- **Duration**: 5 months
- **Competition**: September 2021
