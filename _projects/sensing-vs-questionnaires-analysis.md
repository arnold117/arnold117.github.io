---
layout: page
title: Can Passive Sensing Replace Questionnaires for Mental Health Prediction?
description: Three-study head-to-head comparison (N=1,559) of personality questionnaires vs. continuous passive smartphone/wearable sensing across 15 study–outcome combinations (mental health and academic)
# img: assets/img/sensing-vs-questionnaires.jpg
importance: 2
category: ai-health
toc:
  sidebar: left
---

> **Status**: Manuscript under review at *IEEE Journal of Biomedical and Health Informatics* (JBHI).

## Overview

A three-study head-to-head comparison across three universities (N=1,559) testing whether weeks of continuous passive smartphone and wearable sensing can replace brief personality questionnaires for predicting mental health and academic performance. The central finding: **personality beats sensing in all 11 primary comparisons**, and sensing adds almost nothing beyond personality. The result holds across traditional ML, deep learning (MLP, 1D-CNN), and time-series foundation-model embeddings (MOMENT).

## Research Question

Despite a decade of investment in passive sensing for mental health, the premise that behavioral signals from phones and wearables can replace or augment self-report has rarely been tested against a brief questionnaire in the same people. This project asks the head-to-head question: under what conditions, if any, does passive sensing add value beyond a brief personality questionnaire?

## Studies

| | Study 1: StudentLife | Study 2: NetHealth | Study 3: GLOBEM |
|---|---|---|---|
| **University** | Dartmouth (2013) | Notre Dame (2015–2019) | U. Washington (2018–2021) |
| **N** | 28 | 722 | 809 |
| **Personality** | BFI-44 | BFI-44 | BFI-10 |
| **Sensing** | 13 modalities, 87 features | Fitbit + comm logs, 28 features | Fitbit + phone + GPS, 19 features + 2,597 RAPIDS |
| **MH outcomes** | PHQ-9, PSS, Loneliness | CES-D, STAI, BAI, Loneliness, Self-esteem | BDI-II, STAI, PSS-10, CESD, UCLA |
| **Academic** | GPA | GPA | — |

Together: 3 universities, 3 time periods (2013–2021), 15 study–outcome combinations, 4 ML algorithms plus deep learning, and 44 robustness analyses.

## Key Results

### Questionnaires dominate at the population level

- Personality wins **all 11 primary comparisons** (14/15 including the exploratory 28-person sample; the one exception, Study 1 PHQ-9, is attributed to small-sample overfitting). Personality-only R² = .08–.54; sensing-only R² ≤ .01 in every primary comparison
- Two BFI Neuroticism items, selected inside nested CV, reach R² = .36 for Study 2 depression (CES-D) vs. −.12 for 28 raw sensing features. One of the items overlaps almost completely with depression-scale content, so this marks the ceiling of personality's construct-proximity advantage, not a recommended screening protocol
- **Neuroticism** is the top SHAP predictor in all **8** mental-health study–outcome–model combinations of Studies 2–3
- **Conscientiousness** is the top SHAP predictor of GPA across all four model types in the two samples with registrar GPA (Studies 1–2)
- Deep learning does not rescue sensing: MLP, 1D-CNN and MOMENT never beat Ridge; MOMENT foundation-model embeddings R² = −1.0 to −1.7
- Sensing features are **highly reliable** (ICC(3,k) = 0.73–0.98) — the problem is construct relevance, not measurement quality

### Sensing adds little beyond personality

- Sensing added significant value in **1/8** incremental-validity tests (Study 3 BDI-II, ΔR² = .024) and **0/5** DeLong AUC tests after Benjamini–Hochberg FDR
- None of the 44 robustness analyses changed the result; results stayed flat across 7–92-day windows

### Within-person signal

In a time-aligned panel (weekly PHQ-4 matched to 7-day sensing windows; 3,149 person-weeks), sensing reached R² = .011 vs. personality .072. Within person, however, 17% of participants (N = 392) had a person-specific sensing–mood R² > .30, so sensing may still be useful for individually calibrated monitoring.

## Methodology

### Pipeline
- **Feature extraction** across 13 modalities for Study 1 (87 features); Fitbit + communication for Study 2 (28); Fitbit + phone + GPS for Study 3 (19 curated + 2,597 RAPIDS)
- **4 ML algorithms** in parallel: Elastic Net, Ridge, Random Forest, SVR; plus MLP, 1D-CNN and MOMENT foundation-model embeddings
- **Repeated 5-fold cross-validation** (5 × 5; leave-one-out for Study 1) with permutation tests; nested F-tests for incremental validity and DeLong tests for AUC, each with Benjamini–Hochberg FDR
- **SHAP analysis** for cross-model feature importance; LPA, mediation, and PLS-SEM for Study 1 supplementary

### Robustness
44 supplementary checks covering reliability, ablation, RAPIDS comparison, idiographic prediction, missingness-as-signal, dose–response (7–92 days), within-person tracking, prospective change, cross-study transfer, residualized prediction, reverse prediction, demographic controls, COVID exclusion, and more.

### Reproducibility
Three universities, four cohorts (GLOBEM INS-W_1 through INS-W_4), two BFI variants, seven mental health instruments.

## Technical Stack

| Component | Technology |
|-----------|------------|
| Language | Python 3.11+ |
| ML | scikit-learn, XGBoost, statsmodels |
| Deep Learning | PyTorch 2.11+ (MPS), 1D-CNN, MOMENT foundation model (`momentfm`) |
| Interpretability | SHAP, permutation importance, PLS-SEM, LPA (Gaussian mixture) |
| Statistics | FDR correction, bootstrap mediation, random-effects meta-analysis |
| Data | StudentLife, NetHealth, GLOBEM (4 cohorts) |

## Project Structure

Five-layer script organization: shared utilities → data preparation → core analyses → robustness checks (44 supplementary analyses) → publication materials. Seven-chapter report covering each study individually, cross-study synthesis, clinical utility, and grand synthesis.

## Limitations

- All three datasets are college-age cohorts; generalization to clinical or older populations is untested
- "Personality wins" reflects between-person prediction at the population level; idiographic deployment remains an open opportunity
- Sensing modalities are heterogeneous across studies (different devices, sampling rates, derived features)
- 27-person Study 1 result for PHQ-9 (sensing R² = 0.20) does not replicate at scale — small-N overfitting cautionary tale

## Authors

Yanuo Zhou (first and co-corresponding author) and Cyrus Su Hui Ho (co-corresponding author), Department of Psychological Medicine, Yong Loo Lin School of Medicine, National University of Singapore.

## GitHub Repository

[sensing-vs-questionnaires-analysis](https://github.com/arnold117/sensing-vs-questionnaires-analysis)

## Timeline

**Duration**: November 2025 – April 2026 (Independent research project). Manuscript submitted to *IEEE JBHI*; currently under review.
