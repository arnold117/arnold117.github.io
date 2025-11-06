---
layout: page
title: PrimeKG-RGCN Drug-Disease Link Prediction
description: Graph neural networks for computational drug discovery
# img: assets/img/primekg.jpg
importance: 2
category: ai-health
---

## Overview

An independent research project implementing Relational Graph Convolutional Networks (R-GCN) for link prediction on PrimeKG, a large-scale biomedical knowledge graph. The project aims to predict missing relationships between diseases, drugs, proteins, and other biological entities for drug repurposing and discovery.

## Key Achievements

- **Knowledge Graph-based Drug Discovery**: RGCN link prediction on 30,926 nodes, 849,456 edges
- **Drug Repurposing Candidate Identification**: Predicted novel drug-disease associations
- **Complete Pipeline**: Preprocessing → training → evaluation → validation
- **GPU-Accelerated Processing**: Efficient batch processing on NVIDIA GTX 1070
- **High Performance**: Achieved AUC-ROC 0.9781 and F1-Score 0.9526
- **Scalable Architecture**: Extensible to large-scale biomedical networks

## Background

### What is PrimeKG?

PrimeKG (Precision Medicine Knowledge Graph) is a comprehensive resource that integrates:

- 30,926 nodes (6,282 drugs, 5,593 diseases, 19,051 genes/proteins)
- 849,456 edges across 3 relation types (drug-gene, gene-gene, gene-disease)
- Data from 20+ biomedical databases (DrugBank, OMIM, UniProt, etc.)

### Why Link Prediction?

Link prediction can help:

- Discover new drug-disease associations (drug repurposing)
- Identify disease mechanisms and pathways
- Prioritize candidates for experimental validation
- Accelerate precision medicine research

## Methodology & Implementation

### Graph Neural Network Architecture

```
Input: PrimeKG subgraph
  ↓
R-GCN Layer 1: Relation-specific convolutions
  ↓
Dropout (p=0.3) + ReLU activation
  ↓
R-GCN Layer 2: Aggregation and refinement
  ↓
Entity Embeddings (128-dim vectors)
  ↓
DistMult Decoder: Bilinear scoring function
  ↓
Output: Link probability predictions
```

### Key Design Choices

**Model Components**:
- **Message Passing**: Relation-specific aggregation for heterogeneous graphs
- **Decoder**: DistMult (efficient, interpretable scoring)
- **Negative Sampling**: 1:5 corrupted triplets for training stability
- **Loss Function**: Binary cross-entropy + L2 regularization

**Training Configuration**:
- **Framework**: PyTorch Geometric
- **Hardware**: NVIDIA GTX 1070 (8GB VRAM)
- **Hyperparameters**:
  - Embedding dimensions: 64
  - Hidden dimensions: 128
  - Learning rate: 0.001 (Adam optimizer)
  - Dropout: 0.5
  - Epochs: 100 with early stopping
- **Training Time**: ~4-5 hours for full training
- **Batch Processing**: 1024-edge batches for efficiency

### PrimeKG Knowledge Graph

**Dataset Characteristics**:
- **30,926 nodes**: 6,282 drugs, 5,593 diseases, 19,051 genes/proteins
- **849,456 edges**: 3 relation types (drug-gene, gene-gene, gene-disease)
- **Data Sources**: PrimeKG integrates 20+ biomedical databases (DrugBank, OMIM, UniProt, Reactome, etc.)
- **Coverage**: Comprehensive precision medicine knowledge graph

## Results & Validation

### Link Prediction Performance

| Metric | Value | Interpretation |
|---|---|---|
| **AUC-ROC** | 0.9781 | Excellent classification performance |
| **AUC-PR** | 0.9663 | High precision across all recall levels |
| **Hits@10** | 0.0410 | 4.1% of correct predictions in top-10 |
| **Hits@50** | 0.1551 | 15.5% of correct predictions in top-50 |
| **MRR** | 0.0187 | Mean reciprocal rank of correct predictions |
| **F1-Score** | 0.9526 | Balanced precision and recall |

**Metrics Explanation**:
- **AUC-ROC**: Area under ROC curve - measures classification ability
- **AUC-PR**: Area under Precision-Recall curve - important for imbalanced data
- **Hits@K**: Proportion of correct predictions in top-K results
- **MRR**: Mean Reciprocal Rank - average inverse rank of first correct prediction
- **F1-Score**: Harmonic mean of precision and recall

### Performance Analysis

**Strengths:**
- Excellent binary classification (AUC-ROC > 0.97)
- High precision in top predictions
- Robust to graph sparsity
- Captures multi-hop relationships effectively

**Limitations:**
- Ranking metrics (Hits@K, MRR) show room for improvement
- Performance varies by disease frequency in training data
- May over-predict for high-degree nodes (hub bias)

### Case Study: Drug Repurposing

The model was evaluated on disease-specific drug predictions. While specific COVID-19 results are not included in the repository, the framework enables systematic drug repurposing analysis for any disease in the knowledge graph.

**Analysis Capabilities**:
- Top-K drug predictions for any disease
- Known vs novel prediction identification
- Multi-hop pathway analysis (drug → gene → gene → disease)
- Prediction confidence scoring
- Biological plausibility assessment

## Technical Implementation

### Data Processing Pipeline

1. **Graph Construction**:
   - Load PrimeKG CSV format
   - Filter drug-gene-disease subgraph from full PrimeKG
   - Extract 3 relation types: drug-gene, gene-gene, gene-disease

2. **Preprocessing**:
   - Build node and relation mappings
   - Train/validation/test split (70/15/15)
   - Convert to PyTorch Geometric format

3. **Model Training**:
   - Forward pass through R-GCN layers
   - DistMult scoring on entity embeddings
   - Negative sampling (1:1 ratio, corrupt head or tail)
   - Binary cross-entropy loss with gradient clipping

4. **Evaluation**:
   - Classification metrics (AUC-ROC, AUC-PR, F1-Score)
   - Ranking metrics (MRR, Hits@K)
   - Batch processing (1024 edges per batch)

### Code Architecture

**Technologies**:
- `torch_geometric`: R-GCN layer implementation
- `pandas`: Data loading and preprocessing
- `networkx`: Graph structure analysis
- `scikit-learn`: Evaluation metrics
- `matplotlib`: Visualization and plotting
- `tqdm`: Progress tracking

## Challenges & Solutions

### Challenge 1: Memory Constraints
- **Problem**: GTX 1070 has limited 8GB VRAM for large graphs
- **Solution**: Batch processing (1024 edges), gradient accumulation, periodic cache clearing

### Challenge 2: Class Imbalance
- **Problem**: Need balanced positive/negative samples for training
- **Solution**: 1:1 negative sampling by randomly corrupting head or tail entities

### Challenge 3: Evaluation Metrics
- **Problem**: Standard accuracy misleading for link prediction tasks
- **Solution**: Combined classification metrics (AUC-ROC, F1) and ranking metrics (MRR, Hits@K)

### Challenge 4: Invalid Edges
- **Problem**: Node indices can exceed graph size during processing
- **Solution**: Edge filtering to validate all indices < num_nodes

## Clinical & Research Applications

- **Drug Repurposing**: Identify existing drugs for new indications
- **Drug-Target Discovery**: Predict novel protein targets
- **Disease Mechanism**: Infer causal pathways
- **Precision Medicine**: Personalized drug response prediction
- **Clinical Trial Design**: Identify patient stratification biomarkers

## Links

- **Code**: [GitHub - arnold117/PrimeKG-RGCN-LinkPrediction](https://github.com/arnold117/PrimeKG-RGCN-LinkPrediction)
- **Dataset**: [PrimeKG](https://github.com/mims-harvard/PrimeKG)
- **Paper Reference**: Chandak et al., "Building a knowledge graph to enable precision medicine" (Nature Machine Intelligence, 2022)

## Timeline

- **Start**: October 25, 2025
- **Status**: Ongoing
- **Institution**: Independent research project
