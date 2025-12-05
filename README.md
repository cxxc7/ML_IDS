```
# **Machine Learning–Based Intrusion Detection System (ML-IDS)**

A complete project implementing a Machine Learning Intrusion Detection System using multiple models—Random Forest, Logistic Regression, SVM, and ANN—built on the CIC-IDS (balanced) dataset.
The system performs **binary classification** (Benign vs Attack) and **multiclass attack-type detection**, with a **4-model ensemble** for robust decision-making.

---

## 🚀 **Project Features**

### ✔️ Multi-Model Intrusion Detection

Implements four ML algorithms:

* **Random Forest (RF)**
* **Logistic Regression (LR)**
* **Support Vector Machine (SVM – RBF)**
* **Artificial Neural Network (ANN)**

### ✔️ Ensemble Voting System

Combines outputs from all four models for improved accuracy and stability.

### ✔️ High Detection Accuracy

* **98.59% Binary Accuracy (RF)**
* **95.30% Multiclass Accuracy (RF)**

### ✔️ Live Detection Demo

Accepts a JSON/network-flow record as input → predicts:

* Benign / Attack
* Attack subtype
* Consolidated **attack family probabilities**

### ✔️ Complete Preprocessing Pipeline

Handles NaN, inf, outliers, scaling, and feature cleaning.
Helps produce **clean and robust ML-ready features**.

---

## 📁 **Project Structure**

```

├── ML_IDS.ipynb        # Full project notebook (training, evaluation, demo)
├── balanceddata.csv    # Cleaned and balanced CIC-IDS dataset
├── model_outputs/      # Confusion matrices, ROC curves, feature importance plots
├── README.md           # Project documentation
└── report/             # PDF project report (isproj.pdf, ML_IDS.pdf)

```

---

## 🧠 **Models Used**

### **1. Random Forest (Best Performer)**

* Handles high-dimensional data
* Robust to noise/outliers
* Captures nonlinear attack patterns
* Provides feature importance
* Highest binary & multiclass accuracy

### **2. Logistic Regression**

* Fast, interpretable, linear baseline
* Performs well on linearly separable classes

### **3. SVM (RBF Kernel)**

* Excellent margin-based classifier
* Strong binary performance
* Captures nonlinear attack boundaries

### **4. Artificial Neural Network (ANN)**

* Learns complex flow patterns
* Supports binary & multiclass outputs
* Used for attack-family probability distribution

---

## 🧩 **Ensemble Logic**

The ensemble system aggregates predictions from all four models:

```

If at least 2 of 4 models predict "Attack" → Final = ATTACK
Else → Final = BENIGN

```

Optional **conservative mode**:

```

If any model outputs P(Attack) ≥ 0.9 → Final = ATTACK

```

Multiclass ANN predictions are grouped into **attack families**:

* DoS, DDoS
* PortScan
* Botnet
* Brute Force (FTP/SSh Patator)
* Web Attacks (XSS, SQLi, Brute Force)
* Infiltration

---

## 📊 **Model Comparison**

| Model               | Binary Accuracy | Multiclass Accuracy |
| ------------------- | --------------- | ------------------- |
| **Random Forest**   | **0.9859**      | **0.9531**          |
| Logistic Regression | 0.9718          | 0.9202              |
| SVM (RBF)           | 0.9671          | 0.8498              |
| ANN                 | 0.9531          | 0.8545              |

The Random Forest model performed best due to:

* Strong handling of noisy/tabular data
* Non-linear pattern detection
* Natural resistance to overfitting
* Superior feature importance behaviour

---

## ▶️ **How to Run**

### **1. Install Dependencies**

```

pip install numpy pandas scikit-learn tensorflow matplotlib seaborn

```

### **2. Open Notebook**

```

jupyter notebook ML_IDS.ipynb

```

### **3. Run All Cells**

This will:

* Preprocess dataset
* Train all models
* Evaluate performance
* Generate confusion matrices, ROC curves, and graphs
* Enable the **live demo prediction function**

### **4. Use Live Prediction Demo**

```

sample_output = run_live_demo_json({
"Destination Port": 80,
" Flow Duration": 20000,
...
})

```

Outputs include:

* Prediction per model
* Final ensemble decision
* Attack family probabilities

---

## 📘 **Dataset Information**

**balanceddata.csv** is derived from the **CIC-IDS-2017/CSE-CIC-IDS-2018** datasets and contains:

* 79 network-flow features
* Benign + multiple attack types
* Balanced distribution for ML training

Features include:

* Packet lengths
* Flow durations
* IAT values
* Header lengths
* TCP flag counts
* Subflow stats

---

## 📚 **References**

1. I. Sharafaldin et al., CIC-IDS Dataset, 2018.
2. Deep Learning for IDS, IEEE Access, 2019.
3. Random Forest IDS – Sensors Journal, 2020.
4. Comparative ML Study for IDS, ICCCS, 2013.
5. Flow-based Traffic Analysis – Computers & Security, 2019.
6. DeepDefense – IEEE INFOCOM, 2017.
7. Splunk SIEM Fundamentals, 2021.
8. IBM Machine Learning for Cybersecurity, 2020.
9. ML Algorithms for Flow-IDS, JIS, 2015.
10. A Deep Learning IDS Model, IEEE TETCI, 2018.

---

## 🏁 **Conclusion**

This project proves that **Machine Learning is extremely effective for modern network intrusion detection**, outperforming traditional signature-based methods by learning behavioural patterns of attacks.
Using RF + LR + SVM + ANN + Ensemble voting, the system provides high accuracy, strong robustness, and real-time detection capability.

---
```
