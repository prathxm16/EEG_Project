# Parkinson's EEG Analysis & Counterfactual Explanations

This project implements a machine learning pipeline for detecting Parkinson's Disease (PD) from EEG signals. It utilizes **Multivariate Direct Mode Decomposition (MDMD)** for feature extraction and a **Linear SVM** for classification. Furthermore, it employs **Counterfactual Explanations** (using the Native Guide method) to provide interpretable insights into *why* a specific segment was classified as PD.

##  Pipeline Overview

1.  **Data Loading & Preprocessing**:
    * Loads EEG data in BIDS format using `mne`.
    * Applies notch filtering (50/60Hz) and resamples to 512Hz.
    * Segments data into 2-second non-overlapping windows.
2.  **Signal Decomposition (MDMD)**:
    * Constructs multichannel Hankel trajectory matrices.
    * Performs SVD to decompose signals into intrinsic **Modes** (Trends/Oscillations).
    * Reconstructs signals using Diagonal Averaging.
3.  **Feature Extraction**:
    * Extracts 3 features per mode/channel: **Frequency ($f_q$), Power ($P_q$), Amplitude ($S_q$)**.
4.  **Classification**:
    * Trains a Linear Support Vector Machine (SVM) with Stratified K-Fold Cross-Validation.
    * Optimizes hyperparameters using Grid Search.
5.  **Explainability (XAI)**:
    * Generates **Counterfactuals**: Finds the minimal changes required to flip a "Parkinson's" prediction to "Healthy."
    * Uses the **Native Guide** method: Interpolates the patient's data towards the nearest existing "Healthy" sample to ensure biological plausibility.

##  Prerequisites

Ensure you have Python 3.8+ and the following libraries installed:

```bash
pip install numpy pandas scipy scikit-learn matplotlib mne joblib
