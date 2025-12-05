# 🚨 Machine Learning–Based Intrusion Detection System (ML-IDS)

![Status](https://img.shields.io/badge/Status-Active-brightgreen)
![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![License](https://img.shields.io/badge/License-MIT-lightgrey)
![ML](https://img.shields.io/badge/ML-Scikit--Learn%20%7C%20TensorFlow-orange)

A complete **Machine Learning Intrusion Detection System (IDS)** built on the **CIC-IDS balanced dataset**, supporting both **binary (Benign/Attack)** and **multiclass attack-type** detection.
Implements **Random Forest, Logistic Regression, SVM (RBF), and ANN** with a **4-model ensemble** providing highly robust predictions.

---

# 📚 Table of Contents

* [Features](#-features)
* [Project Structure](#-project-structure)
* [Models Used](#-models-used)
* [Ensemble Logic](#-ensemble-logic)
* [Performance](#-performance)
* [How to Run](#️-how-to-run)
* [Dataset Info](#-dataset-information)
* [References](#-references)
* [Conclusion](#-conclusion)

---

# 🚀 Features

### ✔ Multi-Model Intrusion Detection

Includes four ML algorithms:

* **Random Forest (RF)**
* **Logistic Regression (LR)**
* **SVM (RBF Kernel)**
* **Artificial Neural Network (ANN)**

### ✔ Ensemble Voting System

Votes across all 4 models for improved accuracy and stability.

### ✔ High Detection Accuracy

* **98.59% Binary Accuracy (RF)**
* **95.30% Multiclass Accuracy (RF)**

### ✔ Live JSON Input Detection Demo

Predicts:

* Benign / Attack
* Attack subtype
* Attack-family probability distribution

### ✔ Full Preprocessing Pipeline

Handles NaN, inf, outliers, scaling, and column cleanup.

---

# 📁 Project Structure

```
├── ML_IDS.ipynb        # All training, evaluation & demo code
├── balanceddata.csv    # Cleaned & balanced CIC-IDS dataset
├── model_outputs/      # Confusion matrices, ROC curves, feature importance plots
├── README.md           # This file
└── report/             # Project reports (isproj.pdf, ML_IDS.pdf)
```

---

# 🧠 Models Used

### **1. Random Forest (Best Performer)**

* Excellent handling of tabular, high-dimensional data
* Robust to noise/outliers
* Captures nonlinear attack patterns
* Provides feature importance

### **2. Logistic Regression**

* Fast & interpretable baseline
* Good performance on linearly separable data

### **3. SVM (RBF Kernel)**

* Strong margin-based classifier
* Captures nonlinear decision boundaries

### **4. Artificial Neural Network (ANN)**

* Learns complex flow patterns
* Binary + multiclass support
* Generates attack-family probability distributions

---

# 🧩 Ensemble Logic

### **Main Decision Policy**

```text
If 2 or more models predict “Attack” → Final = ATTACK  
Else → Final = BENIGN
```

### **Conservative Mode**

```text
If any model outputs P(Attack) ≥ 0.9 → Final = ATTACK
```

### **Attack-Type Grouping (ANN)**

* DoS / DDoS
* PortScan
* Botnet
* Brute Force (FTP/SSH Patator)
* Web Attacks (XSS, SQLi, BF)
* Infiltration

---

# 📊 Performance

| Model               | Binary Accuracy | Multiclass Accuracy |
| ------------------- | --------------- | ------------------- |
| **Random Forest**   | **0.9859**      | **0.9531**          |
| Logistic Regression | 0.9718          | 0.9202              |
| SVM (RBF)           | 0.9671          | 0.8498              |
| ANN                 | 0.9531          | 0.8545              |

**Why RF performs best:**

* Nonlinear modeling strengths
* Noise tolerance
* Reduced overfitting risk
* Strong feature importance behavior

---

# ▶️ How to Run

## 1. Install Dependencies

```bash
pip install numpy pandas scikit-learn tensorflow matplotlib seaborn
```

## 2. Open the Notebook

```bash
jupyter notebook ML_IDS.ipynb
```

## 3. Run All Cells

This will:

* Preprocess data
* Train all models
* Evaluate accuracy
* Generate graphs (ROC, confusion matrices, importance plots)
* Enable **live JSON prediction**

## 4. Example: Live Prediction Demo

```python
sample_output = run_live_demo_json({
    "Destination Port": 80,
    " Flow Duration": 20000,
    ...
})
```

Outputs:

* Per-model prediction
* Final ensemble result
* Attack-family probabilities

---

# 📘 Dataset Information

**balanceddata.csv** is derived from **CIC-IDS-2017** and **CSE-CIC-IDS-2018** datasets.

Contains:

* **79 flow-based features**
* Balanced benign/attack classes
* Attack types include DoS, DDoS, PortScan, Web Attacks, Botnet, Infiltration, Brute Force, etc.

Feature groups include:

* Packet length statistics
* Flow durations
* IAT (Inter-Arrival Time) stats
* Header/TCP flag metrics
* Subflow stats

---

# 📚 References

(Shortened & standardized for GitHub)

1. Sharafaldin et al., *CIC-IDS-2017 Dataset*, 2018
2. IEEE Access, *Deep Learning for IDS*, 2019
3. Sensors Journal, *Random Forest for IDS*, 2020
4. ICCCS, *Comparative ML Study for IDS*, 2013
5. Computers & Security, *Flow-Based Traffic Analysis*, 2019
6. INFOCOM, *DeepDefense*, 2017
7. Splunk SIEM Fundamentals, 2021
8. IBM ML for Cybersecurity, 2020
9. JIS, *ML Algorithms for Flow IDS*, 2015
10. IEEE TETCI, *Deep Learning IDS*, 2018

---

# 🏁 Conclusion

This project shows that **Machine Learning is highly effective for modern network intrusion detection**, outperforming traditional signature-based systems by learning behavioral patterns in network flows.
Using **RF + LR + SVM + ANN + Ensemble**, the system achieves:

* High accuracy
* Strong robustness
* Real-time detection capability

Making it suitable for production-grade IDS research and deployment.
