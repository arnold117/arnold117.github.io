---
title: "PrimeKG-RGCN Link Prediction"
date: 2024-08-20
featured: true
# thumb: /images/project-thumbs/primekg.jpg
summary: "Graph neural network implementation for link prediction on PrimeKG, a large-scale biomedical knowledge graph. Explored R-GCN architectures to predict missing relationships between diseases, drugs, and biological entities."
tags: [graph-ml, knowledge-graph, biomedical-ai, deep-learning]
links:
  - text: Code
    url: https://github.com/arnold117/primekg-rgcn
  - text: Dataset
    url: https://github.com/mims-harvard/PrimeKG
  - text: Report
    url: /files/primekg_report.pdf
---

## Overview

This project applies **Relational Graph Convolutional Networks (R-GCN)** to the **PrimeKG** biomedical knowledge graph for link prediction. The goal is to predict missing or未来 relationships between diseases, drugs, proteins, and other biological entities.

## Background

### What is PrimeKG?

PrimeKG (Precision Medicine Knowledge Graph) is a comprehensive resource that integrates:

- 129,000+ nodes (diseases, drugs, proteins, pathways, etc.)
- 4.2M+ edges across 30 relation types
- Data from 20+ biomedical databases (DrugBank, OMIM, UniProt, etc.)

### Why Link Prediction?

Link prediction can help:

- Discover new drug-disease associations (drug repurposing)
- Identify disease mechanisms and pathways
- Prioritize candidates for experimental validation
- Accelerate precision medicine research

## Methodology

### Graph Neural Network Architecture

```
Input: PrimeKG subgraph
  ↓
R-GCN Layer 1 (relation-specific convolutions)
  ↓
Dropout + ReLU
  ↓
R-GCN Layer 2
  ↓
Entity Embeddings
  ↓
DistMult Decoder (for link prediction)
  ↓
Output: Predicted edge probabilities
```

### Key Design Decisions

- **Model:** R-GCN (handles heterogeneous edge types)
- **Decoder:** DistMult (efficient bilinear scoring)
- **Negative Sampling:** Corrupted triplets (1:5 ratio)
- **Loss Function:** Binary cross-entropy with L2 regularization

### Training Setup

- **Framework:** PyTorch Geometric
- **Hardware:** NVIDIA RTX 3090 (24GB VRAM)
- **Training Time:** ~6 hours for full graph
- **Hyperparameters:**
  - Hidden dim: 128
  - Learning rate: 0.001
  - Dropout: 0.3
  - Epochs: 100

## Results

### Link Prediction Performance

| Metric  | Drug-Disease | Protein-Disease | Drug-Protein |
| ------- | ------------ | --------------- | ------------ |
| MRR     | 0.342        | 0.287           | 0.419        |
| Hits@10 | 0.521        | 0.458           | 0.634        |
| Hits@1  | 0.201        | 0.164           | 0.289        |

### Case Study: Drug Repurposing

Top 10 predicted drug-disease associations for COVID-19 included:

- **Remdesivir** (known treatment, correctly predicted)
- **Dexamethasone** (known treatment, correctly predicted)
- **Metformin** (literature-supported, novel prediction)
- **Colchicine** (clinical trials ongoing, novel prediction)

## Implementation Details

The project is implemented in **Python** with:

- `torch_geometric` for R-GCN layers
- `networkx` for graph preprocessing
- `pandas` for data loading and analysis
- `scikit-learn` for evaluation metrics

Key code snippets available in the [GitHub repository](https://github.com/arnold117/primekg-rgcn).

## Challenges & Learnings

### Challenges

1. **Memory constraints:** Full PrimeKG doesn't fit in GPU memory → used subgraph sampling
2. **Class imbalance:** Far more negative examples than positive → weighted loss
3. **Evaluation metrics:** Standard accuracy misleading → focused on MRR and Hits@K

### Key Learnings

- Relation-specific message passing is crucial for heterogeneous graphs
- Pre-training on auxiliary tasks (e.g., node classification) improves results
- Interpretability matters: attention mechanisms help explain predictions

## Future Directions

- **Attention Mechanisms:** Add R-GAT layers for interpretable predictions
- **Temporal Dynamics:** Incorporate temporal information (when relationships emerged)
- **Multi-Task Learning:** Joint prediction of multiple relation types
- **Explainability:** Use GNNExplainer to identify important subgraphs

## References

- Chandak et al., "Building a knowledge graph to enable precision medicine" (2022)
- Schlichtkrull et al., "Modeling Relational Data with Graph Convolutional Networks" (2018)

---

**Keywords:** Graph Neural Networks, Knowledge Graphs, Biomedical AI, Link Prediction, Drug Repurposing, R-GCN
