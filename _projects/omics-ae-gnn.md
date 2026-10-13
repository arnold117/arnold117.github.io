---
layout: page
title: Multi-Omics Integration with Autoencoders and Graph Neural Networks
description: Multi-evidence framework for ranking candidate biosynthetic-pathway genes via dual autoencoders and Graph Attention Networks
# img: assets/img/omics-ae-gnn.jpg
importance: 4
category: ai-health
github: https://github.com/arnold117/omics-ae-gnn
toc:
  sidebar: left
---

## Overview

Open-source computational framework for ranking candidate biosynthetic-pathway genes by integrating transcriptomic and metabolomic data through deep learning, with very few samples (n = 21). The system combines statistical correlation, autoencoder and graph-attention importance, and gene-family homology into one multi-evidence ranking to reduce false positives among candidates.

**Key Idea**: combine several kinds of evidence — correlation, autoencoder importance, graph-attention importance and gene-family evidence — into one candidate ranking, rather than relying on a single method.

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
- Encoder: ~132K → 2,048 → 512 → 128 → 64 (symmetric decoder)
- Regularization: latent L2 penalty, early stopping (patience 15) on a single 80/20 split

**Metabolite Autoencoder (30.9M parameters)**:
- Encoder: ~7K → 2,048 → 512 → 128 → 64 (symmetric decoder)
- Regularization: latent L2 penalty, early stopping (patience 15) on a single 80/20 split

### Graph Attention Network
- Operates on concatenated 128-dim latent vectors (64 gene + 64 metabolite)
- Multi-task classification for tissue/geographic metadata
- Classification accuracy is training accuracy on a transductive graph, so it does not by itself validate the latent representations

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
- Gene AE compresses ~132K genes to a 64-d latent under a ~6.6K:1 feature-to-sample ratio
- Metabolite AE compresses ~7K metabolites to a 64-d latent
- Sample-level GAT uses the latents for auxiliary tissue / origin classification

### Design Rationale
1. **Large-scale autoencoders** with a latent L2 penalty and early stopping for an extreme feature-to-sample ratio (~6.6K:1)
2. **Multi-evidence triangulation** to reduce false positives relative to any single method
3. **Rank-based fusion** to combine heterogeneous evidence types

## Technical Stack

| Component | Technology |
|-----------|------------|
| Language | Python 3.8+ |
| Deep Learning | PyTorch 2.0+ |
| Graph Networks | Graph Attention Network (GAT) |
| Hardware | MPS (Apple Silicon) / CUDA / CPU |
| Configuration | YAML-based pipeline management |
| Analysis | scikit-learn, scipy.stats (Pearson correlation) |
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

**Project Status**: Completed (December 2025 - February 2026)
**Technologies**: PyTorch, GAT, Python
**Category**: AI for Health, Computational Biology, Biosynthetic Pathway Gene Ranking
