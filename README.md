# Network Traffic Anomaly Detection using ML & Deep Learning

This project presents a **comparative study of supervised, unsupervised, and deep unsupervised machine learning techniques** for **network intrusion and anomaly detection**.

The framework is evaluated on the **NSL-KDD dataset**, modeling realistic network monitoring scenarios where **labeled attack data may be scarce or unavailable**.

---

## Objectives
- Detect anomalous (malicious) network traffic under **limited supervision**
- Compare **classical ML vs deep learning** approaches
- Analyze **precision–recall tradeoffs** relevant to intrusion detection systems
- Identify models suitable for **real-world intelligent network deployment**

---

## Dataset
- **NSL-KDD** (KDDTrain+ / KDDTest+)
- 41 network traffic features
- Binary formulation:
  - `0` → Normal traffic
  - `1` → Attack (anomaly)

---

## Models Implemented

### Supervised (Label-Dependent)
- **Logistic Regression**
- **Random Forest**

Used as **upper-bound performance references** when labeled data is available.

### Unsupervised (Label-Free)
- **Isolation Forest**
- **One-Class SVM**

Trained **only on normal traffic**, reflecting realistic deployment constraints.

### Deep Unsupervised
- **LSTM Autoencoder**
  - Learns nonlinear representations of normal network behavior
  - Uses **reconstruction error** as anomaly score
  - Threshold selected via **95th percentile of validation normal traffic**

---

## Methodology
1. Data preprocessing:
   - One-hot encoding (categorical features)
   - Standardization (numerical features)
2. Train/validation/test split without leakage
3. Supervised model training (baseline)
4. Unsupervised training using **normal traffic only**
5. Evaluation using:
   - Confusion matrices
   - Precision–Recall curves
   - ROC-AUC
6. Comparative system-level analysis

---

## Key Results (Validation Set)

| Model | Type | ROC-AUC | Key Insight |
|------|-----|--------|------------|
| Logistic Regression | Supervised | ~0.996 | Strong linear baseline |
| Random Forest | Supervised | ~0.999 | Near-perfect with labels |
| Isolation Forest | Unsupervised | ~0.98 | Lightweight, higher missed attacks |
| One-Class SVM | Unsupervised | ~0.95 | Conservative detection |
| **LSTM Autoencoder** | **Deep Unsupervised** | **~0.98** | Best balance without labels |

**Key finding:**  
> LSTM Autoencoders reduce missed attacks by ~45% compared to Isolation Forest while maintaining high detection accuracy, without relying on labeled attack data.

---

## Evaluation Metrics
- Precision, Recall, F1-score
- ROC-AUC
- Precision–Recall curves (preferred for anomaly detection)
- Confusion matrices for detailed error analysis

---

## Tech Stack
- Python, NumPy, Pandas
- scikit-learn
- TensorFlow / Keras
- Matplotlib
- Google Colab

---
