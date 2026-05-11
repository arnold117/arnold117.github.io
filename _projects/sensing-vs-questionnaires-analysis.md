---
layout: page
title: Can Passive Sensing Replace Questionnaires for Mental Health Prediction?
description: Three-study head-to-head comparison (N=1,559) of personality questionnaires vs. continuous passive smartphone/wearable sensing across 15 mental health and academic outcomes
# img: assets/img/sensing-vs-questionnaires.jpg
importance: 2
category: ai-health
toc:
  sidebar: left
---

> **Status**: Manuscript under review at *IEEE Journal of Biomedical and Health Informatics* (JBHI).

## Overview

A three-study head-to-head comparison across three universities (N=1,559) testing whether weeks of continuous passive smartphone and wearable sensing can replace brief personality questionnaires for predicting mental health and academic performance. The central finding: **two BFI items (10 seconds) outperform 28 sensing features collected over weeks**, and personality questionnaires win 14 of 15 outcome comparisons (93%). The result holds across traditional ML, deep learning (1D-CNN), and time-series foundation models (MOMENT).

## Research Question

Despite a decade of investment in passive sensing for mental health, the field's central premise — that behavioral signals from phones and wearables can replace or augment self-report — has never been rigorously stress-tested at scale against the strongest available baseline. This project asks the head-to-head question: under what conditions, if any, does passive sensing add value beyond a brief personality questionnaire?

## Studies

| | Study 1: StudentLife | Study 2: NetHealth | Study 3: GLOBEM |
|---|---|---|---|
| **University** | Dartmouth (2013) | Notre Dame (2015–2019) | U. Washington (2018–2021) |
| **N** | 28 | 722 | 809 |
| **Personality** | BFI-44 | BFI-44 | BFI-10 |
| **Sensing** | 13 modalities, 87 features | Fitbit + comm logs, 28 features | Fitbit + phone + GPS, 19 features + 2,597 RAPIDS |
| **MH outcomes** | PHQ-9, PSS, Loneliness, Flourishing, PANAS | CES-D, STAI, BAI | BDI-II, STAI, PSS-10, CESD, UCLA |
| **Academic** | GPA | GPA | — |

Together: 3 universities, 3 time periods (2013–2021), 15 outcomes, 4 ML algorithms plus deep learning, and 41 robustness analyses.

## Key Results

### Questionnaires dominate at the population level

- Personality wins **14/15 outcome comparisons (93%)**, mean R² = 0.126 vs. sensing mean R² = −0.153
- **Two BFI items** (10 seconds, R² = 0.36 for CES-D) outperform **28 sensing features** collected over weeks (R² = −0.16)
- **Neuroticism** ranks #1 SHAP feature in **28/28** mental health models across all three studies
- **Conscientiousness** ranks #1 for GPA in **8/8** models
- Deep learning cannot rescue sensing: 1D-CNN R² = −0.03 to −0.10; MOMENT foundation-model embeddings R² = −1.0 to −1.7
- Sensing features are **highly reliable** (ICC(3,k) = 0.73–0.98) — the problem is construct relevance, not measurement quality

### Sensing has value under specific conditions

| Condition | Evidence | Effect size |
|-----------|----------|-------------|
| Lagged early warning | Autoregressive + sensing beats autoregressive alone | +0.031 R² |
| Communication metadata | SMS/call logs improve depression prediction (S2) | +0.030 R² |
| Sleep + nonlinear models | RF captures sleep–anxiety link (S2) | +0.055 R² |
| Idiographic monitoring | 17% of individuals show person-specific R² > 0.3 | Variable |
| Engagement signal | Device non-wear correlates with anxiety | r = −0.12 |
| Clinical classification | Pers + Beh AUC over Pers-only (S2) | +0.06–0.08 AUC |

### Reframing passive sensing

Within-person centered R² ≈ 0 across 3,149 person-weeks of weekly PHQ-4 and EMA. But per-person mean |r| = 0.33–0.35 between mood and concurrent sensing, with 17% of individuals showing idiographic R² > 0.3. The implication: passive sensing is not a **nomothetic** screening tool (one model fits all) but a potential **idiographic** monitoring tool requiring individual calibration — fundamentally changing the field's value proposition.

## Methodology

### Pipeline
- **Feature extraction** across 13 modalities for Study 1 (87 features); Fitbit + communication for Study 2 (28); Fitbit + phone + GPS for Study 3 (19 curated + 2,597 RAPIDS)
- **4 ML algorithms** in parallel: Elastic Net, Ridge, Random Forest, SVR; plus MLP with Optuna, 1D-CNN, MOMENT foundation model, and stacking ensembles
- **5-fold cross-validation** with nested CV for hyperparameter tuning; FDR correction across all tests
- **SHAP analysis** for cross-model feature importance; LPA, mediation, and PLS-SEM for Study 1 supplementary

### Robustness
44 supplementary checks covering reliability, ablation, RAPIDS comparison, idiographic prediction, missingness-as-signal, dose–response (7–92 days), within-person tracking, prospective change, cross-study transfer, residualized prediction, reverse prediction, demographic controls, COVID exclusion, and more.

### Reproducibility
Three universities, four cohorts (GLOBEM INS-W_1 through INS-W_4), two BFI variants, seven mental health instruments — convergent findings across every dimension tested.

## Practical Implication

> Screen with a brief questionnaire (2–5 items, 10 seconds–1 minute); deploy sensing only for high-risk individuals where personalized monitoring may add idiographic value.

This inverts the dominant deployment model in digital mental health, which treats sensing as the primary signal and questionnaires as ground truth.

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
- 28-person Study 1 result for PHQ-9 (sensing R² = 0.468) does not replicate at scale — small-N overfitting cautionary tale

## Supervision

**Supervisor**: Asst Prof Cyrus Ho Su Hui, Department of Psychological Medicine, Yong Loo Lin School of Medicine, National University of Singapore. Assistant Dean (Student Life and Wellbeing), NUS Graduate School; Senior Consultant Psychiatrist, NUH; Clarivate Highly Cited Researcher (2021–2023).

## GitHub Repository

[sensing-vs-questionnaires-analysis](https://github.com/arnold117/sensing-vs-questionnaires-analysis)

## Timeline

**Duration**: November 2025 – April 2026 (Independent research project). Manuscript submitted to *IEEE JBHI*; currently under review.
