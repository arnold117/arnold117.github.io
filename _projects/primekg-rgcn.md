---
layout: page
title: PrimeKG GNN Drug–Target Link Prediction
description: Multi-architecture GNN benchmark for drug–target (drug–gene) link prediction on a biomedical knowledge graph
# img: assets/img/primekg.jpg
importance: 3
category: ai-health
toc:
  sidebar: left
---

## Overview

Reproducible GNN link-prediction pipeline comparing five GNN architectures (RGCN, GCN, GAT, GraphSAGE, GIN) and an MLP baseline on a PrimeKG subgraph for predicting drug–target (drug–gene) links. Early scores that looked too good were traced to a split-level leak (71.5% of test edges had their reverse edge in training) and easy random negatives; Version 2.0 rebuilt the split to be undirected-edge-aware, dropped the inflated numbers, and adopted a standard degree-matched hard-negative protocol.

**Key Finding**: Under this protocol (each test edge ranked against 50 negatives), GAT ranked best of the six models (AUC-ROC 0.9866).

## Problem Statement

Drug discovery is time-consuming and expensive. Knowledge graph-based link prediction can identify candidate drug–target associations by analyzing multi-hop relationships between drugs, diseases, genes, and proteins, accelerating drug repurposing and precision medicine.

## Methodology

### PrimeKG Knowledge Graph
- **Source**: 4.5M relationships from 20 biomedical sources (DrugBank, OMIM, UniProt, Reactome)
- **Processed Graph**: 30,926 nodes (6,282 drugs, 5,593 diseases, 19,051 genes/proteins)
- **Edges**: 854,278 across 3 relation types (drug-gene, gene-gene, gene-disease)
- **Split**: 70/15/15 split of the drug–gene edges only (25,468 unique undirected edges); all other relations stay in the training graph for message passing

### Model Architectures
- **GAT**: Graph Attention Network — learned attention weights
- **RGCN**: Relational GCN — relation-specific convolutions
- **GIN**: Graph Isomorphism Network — maximally expressive message passing
- **GraphSAGE**: Inductive sampling-based aggregation
- **GCN**: Standard graph convolution baseline
- **MLP**: Non-graph baseline

**Shared Configuration**: 128-dim hidden, 64-dim embeddings, DistMult decoder, dropout 0.5, 50 epochs, batch size 2048

### Data Integrity
- **Version 2.0**: Undirected-edge-aware splitting removes split-level leakage (71.5% of test edges had their reverse in training → 0%)
- **Hard Negative Sampling**: standard degree-matched protocol, 50 same-type negatives per positive (51-way ranking) for strict evaluation

## Results

### Strict Evaluation (Hard Negatives, 50 per positive)

Ranking among 51 candidates; these numbers are not comparable with full-entity-ranking results in the literature.

| Model | AUC-ROC | AP | Hits@10 | MRR |
|-------|---------|-----|---------|-----|
| **GAT** | **0.9866** | **0.7955** | **0.9831** | **0.9031** |
| RGCN | 0.9794 | 0.6697 | 0.9789 | 0.8699 |
| GIN | 0.9774 | 0.6522 | 0.9757 | 0.8613 |
| GraphSAGE | 0.9742 | 0.6394 | 0.9789 | 0.8862 |
| GCN | 0.9657 | 0.5538 | 0.9724 | 0.8640 |
| MLP | 0.6592 | 0.0314 | 0.5234 | 0.2710 |

### Key Insights
1. **GNNs outperform the MLP baseline** (AUC > 0.96 vs. 0.66), though part of this gap may come from test edges being present in the message-passing graph (see Limitations)
2. **GAT ranked best**: higher than RGCN on all metrics under this protocol
3. **Evaluation design matters**: fixing the split-level leak and adopting hard negatives replaced inflated Phase-1 numbers

## Advanced Analyses

- **Path-based explanations** with NLP-generated summaries for interpretability
- **Exploratory disease case studies** ranking drugs by embedding similarity (not a trained drug–disease predictor)
- **Embedding visualization** (t-SNE/UMAP) with clustering analysis
- **Error pattern analysis** and failure mode characterization
- **Graph-based plausibility heuristics** (exploratory)
- **Baseline comparisons** (random, degree-based)
- **Confidence calibration** and performance breakdowns by node type

## Technical Stack

| Component | Technology |
|-----------|------------|
| Deep Learning | PyTorch ≥2.0 |
| Graph Networks | PyTorch Geometric ≥2.3 |
| Graph Algorithms | NetworkX ≥2.8 |
| Visualization | Matplotlib, Seaborn, Plotly, UMAP |
| Metrics | scikit-learn ≥1.3 |
| Hardware | CUDA 11.0+ / Apple MPS / CPU |

## Project Structure

```
src/
├── run_full_analysis.py      # Main orchestrator
├── train.py                  # Multi-model training
├── strict_evaluation.py      # Hard negative sampling
├── case_studies.py           # Disease-specific predictions
├── explain_predictions.py    # Path-based reasoning
├── medical_validation.py     # Graph-structure plausibility heuristics (exploratory)
├── visualize_embeddings.py   # t-SNE/UMAP
├── error_analysis.py         # Error patterns
├── compare_methods.py        # Baseline comparison
└── models/                   # Modular encoder registry
    ├── rgcn.py, gcn.py, gat.py, graphsage.py, gin.py, mlp.py
```

## Applications

- Drug–target prioritisation as an input to downstream repurposing studies
- Drug-target interaction prediction

## Limitations & Future Work

**Current Limitations**:
- Strict evaluation runs message passing over the full graph, which still contains the test edges; this likely favours the GNNs over the MLP baseline. Not yet re-run with a training-only graph
- Limited to 3 relation types from PrimeKG subset
- Disease case studies are exploratory (embedding similarity), with no literature or experimental validation

**Future Directions**:
- Full PrimeKG integration (all relation types)
- Temporal knowledge graph evolution
- Clinical trial outcome integration
- External validation against DrugBank updates

## GitHub Repository

[PrimeKG-RGCN-LinkPrediction](https://github.com/arnold117/PrimeKG-RGCN-LinkPrediction)

## Timeline

**Duration**: October 2025 - February 2026 (Independent research project)
- Phase 1: Single RGCN model with optimization (Oct-Nov 2025)
- Phase 2: Multi-architecture comparison, data leakage fix, strict evaluation (2026)
