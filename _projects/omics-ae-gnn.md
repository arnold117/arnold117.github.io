---
layout: page
title: Multi-Omics Integration with Autoencoders and Graph Neural Networks
description: Multi-evidence framework for biosynthetic pathway gene discovery via dual autoencoders and Graph Attention Networks
# img: assets/img/omics-ae-gnn.jpg
importance: 4
category: ai-health
github: https://github.com/arnold117/omics-ae-gnn
toc:
  sidebar: left
---

## Overview

Computational framework for identifying biosynthetic pathway genes by integrating transcriptomic and metabolomic data through deep learning. The system triangulates three independent evidence sources—statistical correlation, autoencoder feature importance, and sequence homology—into a unified multi-evidence ranking to reduce false positives in candidate gene discovery.

**Key Innovation**: GNN classification accuracy validates that autoencoder-derived importance scores reflect genuine biological signal rather than noise.

## Problem Statement

Discovering genes responsible for metabolite biosynthesis is challenging due to:
- **Ultra-high dimensionality**: Genomic (100K+ features) and metabolomic (10K+ features) data vastly exceed sample sizes
- **Small sample regime**: Typical cohorts have n=20-100 samples due to cost constraints
- **False positive risk**: Single-method approaches lack cross-validation across evidence types
- **Nonlinear relationships**: Gene-metabolite associations involve complex regulatory cascades

## Pipeline Architecture (5 Stages)

### Stage 1 — Data Preparation
- Log2 transformation of FPKM values + z-score standardization
- Metabolite intensity normalization
- Quality control visualizations and sample metadata generation

### Stage 2 — Model Training
- Independent gene and metabolite autoencoder training → 64-dimensional latent representations
- Graph Attention Network (GAT) training on concatenated latent vectors with auxiliary tissue/geographic classification tasks

### Stage 3 — Analysis & Visualization
- Dimensionality reduction: t-SNE, UMAP, PCA on latent embeddings
- Gene-metabolite correlation matrices across all sample conditions

### Stage 4 — Feature Importance Extraction
Three complementary importance metrics:
- **Reconstruction importance**: Per-gene MSE contribution from autoencoder
- **Gradient-based importance**: Backpropagation through encoder layers
- **GNN-to-gene mapping**: Projects latent-space importance back to individual genes via correlation weights

### Stage 5 — Multi-Evidence Ranking
Weighted rank normalization combining all evidence:
- 0.4 × Correlation score
- 0.3 × Autoencoder importance
- 0.2 × GNN importance
- 0.1 × BLAST/HMM homology bonus

Produces ranked gene lists with supporting documentation per gene family.

## Methodology

### Dual Autoencoder Architecture

**Gene Autoencoder (545M parameters)**:
- Encoder: 132,129 → 8,192 → 1,024 → 128 → 64
- Decoder: 64 → 128 → 1,024 → 8,192 → 132,129
- Regularization: Dropout (0.3), Early Stopping (patience=10), 5-fold CV

**Metabolite Autoencoder (30.8M parameters)**:
- Encoder: 6,980 → 1,024 → 256 → 64
- Decoder: 64 → 256 → 1,024 → 6,980
- Regularization: Dropout (0.3), Early Stopping (patience=10), 5-fold CV

### Graph Attention Network
- Operates on concatenated 128-dim latent vectors (64 gene + 64 metabolite)
- Multi-task classification for tissue/geographic metadata
- **Validation logic**: High classification accuracy → latent representations capture real biological variation → AE importance scores are biologically meaningful

### Multi-Evidence Scoring
- Rank-based normalization ensures fair contribution from evidence types at different scales
- Latent-correlation mapping preserves interpretability back to biological features
- Gene family integration supports post-hoc BLAST/HMM result incorporation

## Key Features

- **Modular pipeline**: Run individual stages or complete workflows
- **Hardware abstraction**: Automatic detection of MPS (Apple Silicon), CUDA, or CPU
- **Gene family integration**: Post-hoc BLAST/HMM incorporation with batch processing
- **Configurable weights**: Customizable evidence combination via YAML config
- **Checkpoint system**: Intermediate model state preservation
- **Publication-quality output**: 300 DPI figures, CSV tables, Excel-formatted rankings

## Results

### Model Performance
- Gene AE captures major transcriptomic variation despite 6,619:1 feature-to-sample ratio
- Metabolite AE successfully compresses metabolomic profiles into meaningful latent space
- GAT classification validates biological signal in learned representations

### Key Findings
1. **Large-scale autoencoders** handle extreme feature-to-sample ratios (6,619:1) through extensive regularization
2. **Multi-evidence triangulation** reduces false positives compared to single-method approaches
3. **GNN validation** confirms that learned representations capture genuine biological structure
4. **Rank-based fusion** fairly combines heterogeneous evidence types

## Technical Stack

| Component | Technology |
|-----------|------------|
| Language | Python 3.8+ |
| Deep Learning | PyTorch 2.0+ |
| Graph Networks | Graph Attention Network (GAT) |
| Hardware | MPS (Apple Silicon) / CUDA / CPU |
| Configuration | YAML-based pipeline management |
| Analysis | scikit-learn, scipy.stats (Spearman + FDR) |
| Visualization | t-SNE, UMAP, PCA (publication-quality) |

## Privacy & Ethics

- **No biological identifiers**: Sample names, patient IDs removed
- **Feature anonymization**: Specific gene/metabolite names withheld in public repository
- **Aggregated reporting**: Only statistical summaries and framework architecture shared
- **Collaborative approval**: Data provider explicitly approved open-source release

## Limitations & Future Work

### Current Limitations
- **Small sample size** (n=21): Limits generalizability; recommend n≥100 for production
- **Specific biological context**: Associations may not generalize across tissues/conditions
- **Computational cost**: 545M-parameter models require GPU acceleration

### Future Directions
1. Scaling to larger cohorts (n≥100)
2. Transfer learning with public datasets (TCGA, GTEx)
3. Attention mechanisms for relation-specific interpretability
4. Multi-modal extension (proteomics, epigenomics, clinical variables)
5. Federated learning for multi-institution collaboration

## Code Availability

**GitHub Repository**: [omics-ae-gnn](https://github.com/arnold117/omics-ae-gnn)

**Note**: Specific biological data not included to protect collaborator privacy. Framework designed for generalizability across datasets.

---

**Project Status**: Ongoing (December 2025 - Present)
**Technologies**: PyTorch, GAT, Python
**Category**: AI for Health, Computational Biology, Biosynthetic Pathway Discovery
