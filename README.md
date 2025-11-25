# EEG Signal Processing & Machine Learning Pipeline

This repository contains a complete end-to-end workflow for EEG signal processing, time–frequency decomposition, feature engineering, and machine-learning classification. The pipeline is implemented in a single Jupyter notebook (`main.ipynb`) and includes data preparation, modeling, evaluation, and explainability tools.

---

## 📌 Features

### **1. Data Preprocessing**
- Filtering (bandpass 0.5–70 Hz, notch filters, etc.)
- Channel cleaning & metadata handling
- Signal normalization
- Segmentation into fixed-length windows (e.g., 2-second windows)

### **2. Signal Decomposition**
- Multi-mode decomposition (MDMD-style / empirical mode methods)
- Extraction of intrinsic modes (IMFs)
- Reconstruction of filtered signals from selected modes
- Visualization of decomposed components

### **3. Feature Engineering**
- Time-domain features (RMS, variance, Hjorth parameters, etc.)
- Frequency-domain features (FFT-based bands)
- Entropy-based features
- Outputs consolidated into a labeled DataFrame for ML

### **4. Machine Learning**
Includes models such as:
- Logistic Regression  
- Random Forest  
- SVM  
- XGBoost / Gradient Boosting  
- Cross-validation (StratifiedKFold)  
- Hyperparameter tuning (GridSearchCV)

Evaluation metrics:
- Accuracy, Precision, Recall, F1
- ROC-AUC
- Confusion Matrix
- Matthews Correlation Coefficient (MCC)

### **5. Explainability**
- SHAP-style local explanations
- Counterfactual analysis for individual EEG windows
- Feature importance visualizations

---

