---
layout: page
title: PrimeKG GNN Drug-Disease Link Prediction
description: Multi-architecture GNN benchmark for computational drug repurposing on biomedical knowledge graphs
# img: assets/img/primekg.jpg
importance: 3
category: ai-health
toc:
  sidebar: left
---

## Overview

Comprehensive biomedical link prediction framework comparing 6 GNN architectures (RGCN, GCN, GAT, GraphSAGE, GIN, MLP) on the PrimeKG knowledge graph for predicting drug-disease therapeutic indications. Version 2.0 features a critical data leakage fix (71.5% → 0% leakage) with undirected-edge-aware splitting and hard negative evaluation. Best model (GAT) achieves 0.9866 AUC-ROC under strict evaluation.

**Key Finding**: Attention mechanisms (GAT) outperform explicit relation-type modeling (RGCN) for drug-disease link prediction.

## Problem Statement

Drug discovery is time-consuming and expensive. Knowledge graph-based link prediction can identify novel drug-disease associations by analyzing multi-hop relationships between drugs, diseases, genes, and proteins, accelerating drug repurposing and precision medicine.

## Methodology

### PrimeKG Knowledge Graph
- **Source**: 4.5M relationships from 20+ biomedical databases (DrugBank, OMIM, UniProt, Reactome)
- **Processed Graph**: 30,926 nodes (6,282 drugs, 5,593 diseases, 19,051 genes/proteins)
- **Edges**: 849,456 across 3 relation types (drug-gene, gene-gene, gene-disease)
- **Split**: 70% train (838,882) / 15% val (7,688) / 15% test (7,708)

### Model Architectures
- **GAT**: Graph Attention Network — learned attention weights
- **RGCN**: Relational GCN — relation-specific convolutions
- **GIN**: Graph Isomorphism Network — maximally expressive message passing
- **GraphSAGE**: Inductive sampling-based aggregation
- **GCN**: Standard graph convolution baseline
- **MLP**: Non-graph baseline

**Shared Configuration**: 128-dim hidden, 64-dim embeddings, DistMult decoder, dropout 0.5, 50 epochs, batch size 2048

### Data Integrity
- **Version 2.0**: Undirected-edge-aware splitting eliminates data leakage (71.5% → 0%)
- **Hard Negative Sampling**: 50 negatives per positive for strict evaluation

## Results

### Strict Evaluation (Hard Negatives, 50 per positive)

| Model | AUC-ROC | AP | Hits@10 | MRR |
|-------|---------|-----|---------|-----|
| **GAT** | **0.9866** | **0.7955** | **0.9831** | **0.9031** |
| RGCN | 0.9794 | 0.6697 | 0.9789 | 0.8699 |
| GIN | 0.9774 | 0.6522 | 0.9757 | 0.8613 |
| GraphSAGE | 0.9742 | 0.6394 | 0.9789 | 0.8862 |
| GCN | 0.9657 | 0.5538 | 0.9724 | 0.8640 |
| MLP | 0.6592 | 0.0314 | 0.5234 | 0.2710 |

### Key Insights
1. **Graph structure is critical**: All GNNs vastly outperform MLP baseline
2. **Attention > Relation modeling**: GAT outperforms RGCN across all metrics
3. **Principled evaluation matters**: Data leakage fix revealed true model capabilities masked by loose protocols

## Advanced Analyses

- **Path-based explanations** with NLP-generated summaries for interpretability
- **Disease-specific case studies** with drug repurposing predictions
- **Embedding visualization** (t-SNE/UMAP) with clustering analysis
- **Error pattern analysis** and failure mode characterization
- **Biological plausibility validation** with evidence gathering
- **Baseline comparisons** (random, degree-based, TransE)
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
├── medical_validation.py     # Biological plausibility
├── visualize_embeddings.py   # t-SNE/UMAP
├── error_analysis.py         # Error patterns
├── compare_methods.py        # Baseline comparison
└── models/                   # Modular encoder registry
    ├── rgcn.py, gcn.py, gat.py, graphsage.py, gin.py, mlp.py
```

## Applications

- Drug repurposing for new therapeutic indications
- Disease mechanism identification via multi-hop reasoning
- Drug-target interaction prediction
- Experimental candidate prioritization
- Precision medicine research

## Limitations & Future Work

**Current Limitations**:
- Strict evaluation reveals ranking challenges masked by loose protocols
- Limited to 3 relation types from PrimeKG subset
- Case study validation limited to literature evidence

**Future Directions**:
- Full PrimeKG integration (all relation types)
- Temporal knowledge graph evolution
- Clinical trial outcome integration
- External validation against DrugBank updates

## GitHub Repository

[PrimeKG-RGCN-LinkPrediction](https://github.com/arnold117/PrimeKG-RGCN-LinkPrediction)

## Timeline

**Duration**: October 2025 - Present (Independent research project)
- Phase 1: Single RGCN model with optimization (Oct-Nov 2025)
- Phase 2: Multi-architecture comparison, data leakage fix, strict evaluation (2026)
