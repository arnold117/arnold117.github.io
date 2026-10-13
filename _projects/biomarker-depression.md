---
layout: page
title: Machine-Learning Screening of Inflammation-Gene Expression for Suicide-Risk Stratification in Depression
description: NUS MSc course project comparing ten ML models on inflammation-gene expression; the models did not generalise to an independent test set
# img: assets/img/biomarker.jpg
importance: 5
category: ai-health
toc:
  sidebar: left
---

## Overview

NUS MSc course project on whether inflammation-gene expression can stratify suicide risk in major depressive disorder (MDD). Compared 10 ML models on expression data from 197 MDD patients and 151 controls: training-set CV accuracy reached ≈ 0.77, but accuracy on an independent test set was 0.44–0.61, so the models did not generalise. NR3C1a and HSPA1B recurred as important features across models.

## Problem Statement

Suicide claims over 700,000 lives globally each year. Current diagnostic methods rely on subjective self-reporting (BSRS-5, C-SSRS), leading to false positives/negatives and inconsistent risk assessment. Despite extensive biomarker research (DNA methylation, RNA expression), clinical implementation remains limited.

## Methodology

### Dataset & Preprocessing

**Training Data**: 197 MDD patients + 151 controls, 32 inflammation-related genes (qPCR RNA expression)  
**Test Data**: Independent suicide ideation dataset for external validation

**Data Processing**:
- KNN imputation for missing values, Min-Max normalization
- Binary classification with two risk stratifications tested
- 5-fold cross-validation across 10 ML models (Random Forest, SVM, XGBoost, etc.)

### Biomarker Identification

**Feature Selection**: Top 3 genes per model based on decision impact  
**Consensus Approach**: Most frequent genes across robust models (CV accuracy > 0.5)  
**Validation**: Differential gene expression analysis with Bonferroni correction, KEGG pathway analysis

## Results

**Training Performance**: Best configuration achieved 0.77 CV accuracy (Set 1)  
**Highlighted Genes**:
- **NR3C1a** (log-fold change 0.374): Glucocorticoid receptor signaling, stress hormone regulation
- **HSPA1B** (log-fold change 0.427): Heat shock protein, cellular stress response
- **ABL1** (log-fold change 0.519): Signal transduction in stress pathways

**Test Set Performance**: External validation showed 0.44-0.61 accuracy (limited generalizability due to small sample size and dataset heterogeneity)

## Limitations & Future Work

**Current Limitations**: Limited test set generalizability (0.44-0.61), small sample size, dataset-specific biases

**Future Directions**:
- Expand datasets with diverse demographics
- Multi-omics integration (protein, metabolic markers)
- Longitudinal biomarker tracking for risk trajectory analysis

## Achievements & Recognition

### Key Metrics
- 10 ML models evaluated across 8 experimental combinations
- NR3C1a and HSPA1B recurred as top features across models
- 0.77 CV accuracy on the training set; 0.44–0.61 on the independent test set

## Team & Collaboration

**Supervisors**: Ashley Lim & Prof. Caroline Lee  
**Institution**: Department of Biochemistry, National University of Singapore

## Timeline

**Duration**: August 2024 - December 2024 (5 months)
