---
layout: page
title: Bedside-Monitor Signal Viewer
description: Course project — Python/PySide6 + QML desktop viewer that decodes a bedside-monitor packet protocol and plots ECG, respiration, temperature, SpO2 and blood pressure in real time
# img: assets/img/ecg-eeg.jpg
importance: 5
category: signal-processing
toc:
  sidebar: left
---

## Overview

Team project in the Biomedical Engineering skills-training course (software track) at Nanchang Hangkong University: a desktop viewer that decodes a bedside-monitor packet protocol and displays five physiological parameters — ECG, respiration, temperature, SpO2 and non-invasive blood pressure — as real-time waveforms.

## Implementation

- **Protocol decoding**: parses the monitor's packet format into per-parameter streams
- **Desktop UI**: PySide6 + QML front end with QtCharts real-time plotting
- **Data source**: recorded monitor data (CSV) replayed in real time

## Related coursework

- QML serial-port assistant and waveform-drawing exercises (Medical Software Design course, 2022)

## Technical Stack

Python, PySide6, Qt/QML, QtCharts

## Timeline

**Duration**: May – June 2022 (course project)
