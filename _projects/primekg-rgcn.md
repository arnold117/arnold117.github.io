---
layout: page
title: PrimeKG-RGCN Drug-Disease Link Prediction
description: Graph neural networks for computational drug discovery
# img: assets/img/primekg.jpg
importance: 2
category: ai-health
toc:
  sidebar: left
---

## Overview

Relational Graph Convolutional Networks (R-GCN) for link prediction on PrimeKG biomedical knowledge graph (30,926 nodes, 849,456 edges). Achieves 0.9781 AUC-ROC for predicting drug-disease associations, enabling computational drug repurposing and discovery.

## Problem Statement

Drug discovery is time-consuming and expensive. Knowledge graph-based link prediction can identify novel drug-disease associations by analyzing relationships between drugs, diseases, genes, and proteins, accelerating drug repurposing and precision medicine.

## Methodology

### PrimeKG Knowledge Graph
- **Nodes**: 30,926 (6,282 drugs, 5,593 diseases, 19,051 genes/proteins)
- **Edges**: 849,456 across 3 relation types (drug-gene, gene-gene, gene-disease)
- **Sources**: 20+ biomedical databases (DrugBank, OMIM, UniProt, Reactome)

### R-GCN Architecture
- **Input**: PrimeKG subgraph
- **Layers**: 2 R-GCN layers (relation-specific convolutions, dropout 0.3, ReLU)
- **Embeddings**: 128-dim entity vectors
- **Decoder**: DistMult bilinear scoring function
- **Training**: PyTorch Geometric, NVIDIA GTX 1070, 1024-edge batches, 100 epochs

## Results

### Baseline Performance
**Link Prediction Performance**:
- AUC-ROC: 0.9696 | AUC-PR: 0.9663 | F1-Score: 0.9526
- Hits@10: 49.1% | Hits@50: 15.5% | MRR: 0.8027
- Mean Rank: 493.53

**Analysis**: Strong binary classification; ranking metrics showed potential for optimization

### Phase 1 Optimization (November 2025)

**Architecture Enhancements**:
- LayerNorm integration after R-GCN convolutions for training stability
- Skip connections between convolutional layers for better gradient flow
- Embedding caching to eliminate redundant computations
- Vectorized batch operations replacing iterative processing

**Performance Improvements**:
- **Classification**: AUC-ROC improved by 2.98% (0.9696 → 0.9985)
- **Ranking**: MRR increased by 19.73% (0.8027 → 0.9611), Hits@10 up 11.89% (49.1% → 61.0%)
- **Efficiency**: Mean Rank decreased 88.10% (493.53 → 58.75)
- **Speed**: Evaluation accelerated 75×, from ~300s to 4s

**Trade-offs**: Precision marginally decreased by 1.07%, but recall improved by 6.94%, resulting in superior overall F1-scores

## Applications

- Drug repurposing for new indications
- Disease mechanism identification
- Drug-target interaction prediction
- Experimental candidate prioritization
- Precision medicine research

## Limitations & Future Work

**Current Limitations**:
- Phase 1: ~50.9% of true edges still fall outside top 10 predictions
- GTX 1070 memory constraints (8GB VRAM)
- Limited to 3 relation types

**Phase 2 Directions**:
- Further ranking optimization for top-k predictions
- Multi-hop pathway analysis
- Biological plausibility scoring
- Clinical validation of predictions

## Achievements & Recognition

### Key Metrics
- **Phase 1**: 0.9985 AUC-ROC for drug-disease link prediction (post-optimization)
- **Performance**: 88% reduction in mean rank, 75× evaluation speedup
- Complete pipeline: preprocessing → training → evaluation → optimization
- GPU-accelerated batch processing (1024 edges/batch)

### Technical Stack
PyTorch Geometric, NetworkX, scikit-learn, pandas, matplotlib

### GitHub Repository
[PrimeKG-RGCN-LinkPrediction](https://github.com/arnold117/PrimeKG-RGCN-LinkPrediction) | [Phase 1 Comparison Results](https://github.com/arnold117/PrimeKG-RGCN-LinkPrediction/blob/main/results_phase1/PHASE1_COMPARISON.md)

## Timeline

**Duration**: October 25, 2025 - Present (Independent research project)
**Phase 1 Optimization**: November 2025 - December 2025