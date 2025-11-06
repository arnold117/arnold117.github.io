---
layout: page
title: Machine Learning Biomarkers for Suicide Risk Assessment in Depression
description: Identifying NR3C1a and HSPA1B as genetic biomarkers for suicide risk in MDD using machine learning and gene expression analysis
# img: assets/img/biomarker.jpg
importance: 3
category: ai-health
toc:
  sidebar: left
---

## Overview

This research investigates machine learning approaches to identify genetic biomarkers associated with suicide risk in patients with major depressive disorder (MDD). By analyzing RNA expression data from 197 MDD patients and 151 controls, the study employed 10 machine learning models to uncover key genetic markers that could advance objective suicide risk assessment.

## Problem Statement

Suicide claims over 700,000 lives globally each year and is a leading cause of death among young adults. Current diagnostic methods rely heavily on subjective self-reporting and clinical judgment, creating significant limitations:

- **Diagnostic Challenges**: Self-reported questionnaires (BSRS-5, C-SSRS) lack precision and are subject to reporting bias
- **False Positives**: May unnecessarily pathologize individuals and cause psychological distress
- **False Negatives**: Could leave vulnerable individuals without critical mental health interventions
- **Clinical Gap**: Extensive research on biomarkers (DNA methylation, RNA expression) remains largely theoretical with limited clinical implementation

## Key Achievements

- **Identified Biomarkers**: NR3C1a and HSPA1B consistently emerged as critical genes across multiple experimental combinations
- **Comprehensive Testing**: Evaluated 10 machine learning models across 8 experimental combinations
- **Differential Expression Analysis**: Confirmed biomarker upregulation with log-fold changes of 0.374 (NR3C1a) and 0.427 (HSPA1B)
- **Robustness Testing**: Tested multiple preprocessing strategies and risk categorization approaches
- **Pathway Analysis**: Linked biomarkers to glucocorticoid signaling and cellular stress response mechanisms
- **Cross-dataset Validation**: External validation on independent suicide ideation dataset

## Methodology

### Dataset

**Training Set**: "Immunological subtypes of depression: insights from monocyte gene expression"
- 32 genes with established inflammation-related signatures
- 197 MDD patients + 151 healthy controls
- Clinical features: age, gender, BMI, depression severity, childhood adversity, suicide risk
- Data type: qPCR RNA expression profiling

**Test Set**: "Brain and blood transcriptome profiles delineate common genetic pathways across suicidal ideation and suicide"
- Independent dataset for generalizability assessment
- Gene reference mapping (ENSG IDs) for consistency

### Preprocessing & Classification

**Data Handling**:
- KNN imputation for missing values
- Min-Max normalization for feature scaling
- Binary classification: Tested two risk stratifications:
  - **Mapping 1**: Class 0 (no risk) vs. Class 1 (low+medium+high risk)
  - **Mapping 2**: Class 0 (no+low risk) vs. Class 1 (medium+high risk)

**Model Evaluation**:
- 5-fold cross-validation for training
- Grid search across 10 ML models (Random Forest, SVM, XGBoost, Logistic Regression, Gradient Boosting, Decision Tree, AdaBoost, LightGBM, CatBoost, MLP)
- Models with CV accuracy < 0.5 excluded from final evaluation
- Metrics: Accuracy, Precision (class 0 & 1), Test set generalization

### Biomarker Identification

**Feature Selection**: Top 3 genes per model identified based on impact on decision-making  
**Biomarker Consensus**: Most frequently occurring genes across robust models selected as candidates

### Analysis Variations

8 experiment combinations tested to assess preprocessing impact:
- Inclusion/exclusion of controls
- Removal of duplicate NR3C1b entry
- Alternative gene mapping strategies
- Different risk category combinations

### Differential Gene Expression

- Bonferroni correction for multiple comparisons
- Log-fold change calculation
- KEGG database pathway analysis for biological context

## Results

### Training Performance

**Best Configuration (Set 1)**: Achieved mean cross-validation accuracy of **0.77**
- Risk mapping distinguishing "low" from "no" risk yielded superior results
- Mean precision: 0.775 (class 0), 0.6575 (class 1)

**Key Finding**: Risk category stratification significantly influenced model performance
- Datasets combining "low, medium, high risk" showed markedly inferior results
- Removing duplicate genes enhanced model interpretability

### Identified Biomarkers

**Primary Biomarkers** (consistent across multiple sets):
- **NR3C1a**: Log-fold change 0.374 | Role in glucocorticoid receptor signaling and stress hormone regulation
- **HSPA1B**: Log-fold change 0.427 | Heat shock protein involved in cellular stress response and neuroprotection

**Secondary Marker**:
- **ABL1**: Log-fold change 0.519 (Sets 1, 3, 5) | Role in cellular signal transduction stress-related pathways

### Test Set Performance

External validation revealed generalizability challenges:
- Test accuracies ranged from **0.44 to 0.61** across model configurations
- Best performer: CatBoost (Set 7) with 0.61 accuracy
- Logistic Regression achieved balanced precision (0.55 class 0, 0.62 class 1)

**Root Causes of Limited Generalization**:
1. Small sample sizes amplifying overfitting
2. Dataset heterogeneity (demographic and clinical variation)
3. Class imbalance introducing systematic biases

### Differential Gene Expression Analysis

**Significant Findings**:
- NR3C1a and HSPA1B consistently upregulated across Sets 1, 3, 5, 7
- Sets 2, 4, 6, 8 (excluding controls or with alternative mappings) showed no statistically significant genes
- Highlights critical importance of preprocessing strategies

## Biological Significance

**NR3C1a** (Glucocorticoid Receptor): Key modulator of stress hormone regulation; dysfunction linked to psychiatric disorders and altered stress response  
**HSPA1B** (Heat Shock Protein 1B): Facilitates cellular stress response and neuroprotective processes; altered expression in stress-related conditions  
**ABL1** (Abelson Murine Leukemia): Involved in cellular signal transduction; potential role in stress-related molecular networks

## Limitations & Future Directions

**Current Limitations**:
- Modest test set generalizability (0.44-0.61 accuracy) limits clinical deployment
- Small sample size and class imbalance affect model robustness
- Dataset-specific biases may constrain predictive capabilities

**Recommended Next Steps**:
1. **Expand Datasets**: Include participants from diverse demographic backgrounds
2. **Multi-omics Integration**: Combine gene expression with protein levels and metabolic markers
3. **Longitudinal Analysis**: Track biomarker changes over time to understand risk trajectory
4. **Hybrid Approach**: Combine machine learning strengths with rigorous statistical validation
5. **External Validation**: Implement comprehensive validation protocols before clinical implementation

## Supervisors

**Ashley Lim** & **Prof. Caroline Lee** - Department of Biochemistry, National University of Singapore

## Timeline

- **Start**: August 2024
- **Completion**: December 2024
- **Duration**: 5 months (Course project at NUS)
