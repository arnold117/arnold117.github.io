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

**Link Prediction Performance**:
- AUC-ROC: 0.9781 | AUC-PR: 0.9663 | F1-Score: 0.9526
- Hits@10: 4.1% | Hits@50: 15.5% | MRR: 0.0187

**Analysis**: Excellent binary classification; ranking metrics show room for improvement (hub bias, graph sparsity)

## Applications

- Drug repurposing for new indications
- Disease mechanism identification
- Drug-target interaction prediction
- Experimental candidate prioritization
- Precision medicine research

## Limitations & Future Work

**Limitations**: GTX 1070 memory constraints (8GB VRAM), ranking metrics lower than classification metrics, limited to 3 relation types

**Future Directions**:
- Multi-hop pathway analysis
- Biological plausibility scoring
- Clinical validation of predictions

## Achievements & Recognition

### Key Metrics
- 0.9781 AUC-ROC for drug-disease link prediction
- Complete pipeline: preprocessing → training → evaluation
- GPU-accelerated batch processing (1024 edges/batch)

### Technical Stack
PyTorch Geometric, NetworkX, scikit-learn, pandas, matplotlib

## Timeline

**Duration**: October 25, 2025 - Present (Independent research project)