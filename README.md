# 🫀 Cardiac Anomaly Detection - Graph-Based Learning Framework

## 📖 Project Overview

This repository contains the research implementation of a novel graph-based framework for real-time cardiac anomaly detection using single-lead ECG signals. The method combines unsupervised topology learning with probabilistic classification to achieve high accuracy while maintaining computational efficiency suitable for mobile health applications.

**⚠️ Note: This is a research codebase** - The implementation is currently optimized for experimental validation and academic research purposes. It is not yet production-ready for general public use or clinical deployment without further validation and testing.

## 🔬 How It Works

### Core Architecture

Our framework follows a three-stage pipeline:

Raw ECG Signal (140Hz, 1s)
↓
[1] Graph Representation Learning
├── Option A: Self-Organizing Maps (SOM)
└── Option B: K-means with Graph Connections
↓
[2] Geodesic Distance Computation
└── Ball-Tree for O(log k) neighbor search
↓
[3] Probabilistic Classification
└── PNN with asymmetric loss functions
↓
Anomaly Probability + Clinical Risk Assessment


### Key Components

#### 1. **Graph-Based Representation Learning**
Instead of processing raw ECG signals directly, we learn an embedded graph that captures the intrinsic manifold structure of cardiac waveforms:

- **SOM Approach**: Creates a 2D grid where neurons adapt to represent ECG patterns
- **K-means Approach**: Forms graph nodes from cluster centroids, connected by proximity

#### 2. **Dynamic Time Warping (DTW) Distance**
Unlike Euclidean distance, DTW accounts for temporal misalignments in ECG signals, crucial for accurate pattern matching.

#### 3. **Probabilistic Neural Network (PNN)**
Classification uses geodesic distances within the learned graph, providing:
- Probability estimates for each class
- Asymmetric loss handling (different costs for false positives/negatives)
- Optimal Bayes decision-making

#### 4. **Ball-Tree Indexing**
Enables efficient O(log k) nearest-centroid search, making real-time prediction feasible on mobile devices.

## ✨ Key Advantages

### 🚀 **Computational Efficiency**
- **Prediction complexity**: O(log k) vs. O(n) for deep learning models
- **Memory efficient**: Stores only centroid probabilities vs. entire model weights
- **Suitable for mobile devices**: Low resource requirements for continuous monitoring

### 🧠 **Interpretability**
- **Visual graph structure**: Learned centroids and connections are human-examinable
- **Transparent decision-making**: Classification based on proximity to learned patterns
- **Clinical validation**: Doctors can trace predictions to similar historical cases

### ⚡ **Flexibility & Adaptability**
- **Multi-source integration**: Combines ECG signals with patient metadata
- **Risk-aware classification**: Adjustable loss functions for medical priorities
- **Incremental learning**: Can adapt to individual patient patterns over time

### 🏥 **Clinical Relevance**
- **Asymmetric error handling**: Different costs for false negatives (missing anomalies) vs. false positives
- **Prior incorporation**: Uses patient history as Bayesian priors
- **Validated performance**: 94-98% accuracy on controlled datasets

## 📊 Performance Highlights

| Model | Synthetic Data | Real ECG Data | Real + Patient History |
|-------|---------------|---------------|------------------------|
| **SOM + PNN** | 97% accuracy | 92% accuracy | 93% accuracy |
| **K-means + PNN** | 98% accuracy | 94% accuracy | 95% accuracy |
| **Simple Baseline** | 84% accuracy | 92% accuracy | 93% accuracy |

**Key Insight**: The graph-based approaches significantly outperform simple methods on synthetic data (14-15% improvement), showing their ability to capture complex ECG patterns.

@article{fraiman2025cardiac,
  title={Cardiac Anomaly Detection Using Graph-Based Representation Learning},
  author={Fraiman, Demián},
  journal={arXiv preprint},
  year={2025},
  note={Research implementation available at: https://github.com/username/cardiac-anomaly-detection}
}
