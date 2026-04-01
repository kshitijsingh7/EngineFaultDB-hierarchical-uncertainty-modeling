# Uncertainty-Aware Hierarchical Engine Fault Diagnosis

A comprehensive machine learning and deep learning pipeline for **engine fault classification**, introducing an **uncertainty-aware hierarchical model with trapezoidal fuzzy logic** to handle ambiguous fault regions.

---

## Overview

This repository presents a complete experimental pipeline based on the **EngineFaultDB dataset**, focusing on:

* Baseline ML models
* Deep learning architectures
* Representation learning (Siamese / embeddings)
* Fault overlap analysis
* **Novel hierarchical fuzzy classification (proposed method)**

The core problem addressed:

> **Why are Fault 2 and Fault 3 difficult to classify?**

---

## Dataset

* Dataset: EngineFaultDB
* Contains real engine sensor readings:

  * MAP, TPS, RPM, AFR, Lambda, CO, HC, etc.
* 4 fault classes:

  ```
  0 → Normal
  1 → Rich Mixture
  2 → Lean Mixture
  3 → Low Voltage
  ```

---

## Key Contributions

* Comprehensive comparison of ML and DL models
* Identification of **feature overlap problem (Class 2 vs 3)**
* Embedding-based representation analysis
* **Uncertainty-aware hierarchical classification**
* Introduction of **Trapezoidal Fuzzy Decision Boundary**

---

## Experiments

### 1️ Baseline Models

* Logistic Regression
* Decision Tree
* Random Forest
* SVM
* KNN
* Naive Bayes

Result:

* High accuracy for classes 0 & 1
* Severe confusion between **class 2 and 3** 

---

### 2️ Deep Learning Models

* Feedforward Neural Network
* CNN
* CNN + LSTM
* TabNet

Insight:

* Deep models improve generalization
* But still struggle on overlapping classes

---

### 3️ Representation Learning

* Siamese Network
* Embedding visualization (PCA / t-SNE)

Finding:

* Class 2 & 3 embeddings overlap heavily → not separable

---

### 4️ Fault Overlap Analysis

* Feature overlap ratio > **95% for most sensors**
* Confirms **data-level ambiguity**, not just model limitation
<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/58304061-f212-4be2-8e86-0eaffd02a156" />

<img width="1489" height="1990" alt="image" src="https://github.com/user-attachments/assets/eb855ad5-92da-4e0a-b7cf-7dea2891d255" />

---

## Proposed Method

### Hierarchical Classification

```
Level 1 → {0, 1, (2,3)}
Level 2 → {2 vs 3}
```

---

### Trapezoidal Fuzzy Logic

Instead of forcing a hard decision:

```
P(Class 2)

0 ── a ────── b ========= c ────── d ── 1
  C3   unsure   ambiguous   unsure   C2
```
<img width="691" height="393" alt="image" src="https://github.com/user-attachments/assets/b1ba1390-f02e-4588-a5b3-9225a2a67eed" />

---

### Key Idea

Introduce:

```
Class 4 → Ambiguous Region
```

---

## Results

| Metric              | Value       |
| ------------------- | ----------- |
| Baseline Accuracy   | ~75%        |
| Confident Accuracy  | **~85–96%** |
| Ambiguous Detection | ~27–31%     |

* Significant improvement in **reliable predictions**
* Avoids incorrect classification in uncertain regions

---

## Example Output

* Confusion matrices
* PCA / t-SNE plots
* Feature overlap graphs
* Fuzzy membership curves

---

## 🛠️ Tech Stack

* Python
* Scikit-learn
* XGBoost
* TensorFlow / Keras
* PyTorch (Siamese Networks)
* TabNet
* Scikit-Fuzzy

---

## Key Insight

> The challenge in fault classification is not model complexity, but **data ambiguity**.

This work demonstrates that:

* Traditional ML fails due to overlapping feature space
* Deep learning learns representations but still struggles
* **Uncertainty modeling is the real solution**

---

## Research Work

This repository is based on the research paper:

**"Uncertainty-Aware Hierarchical Classification for Engine Fault Using Fuzzy Logic and Machine Learning"**

---

## Future Work

* Semi-supervised labeling of ambiguous data
* Probabilistic deep learning
* Bayesian neural networks
* Real-time deployment for engine monitoring systems

---
