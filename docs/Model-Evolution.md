# 📈 Model Evolution & Optimization Report

This document details the transition from a baseline classifier to the final **Linear Support Vector Machine (LSVM)** model, focusing on the technical challenges of K-Pop lyric classification.

## 1. The Baseline: Multinomial Naive Bayes
Initially, a **Multinomial Naive Bayes (MNB)** model was implemented. While computationally efficient, it suffered from two primary issues:
* **The "RM Bias":** Because RM and Suga have significantly larger solo discographies (e.g., *RM*, *Mono*, *Agust D*, *D-2*), the model defaulted to predicting them for any ambiguous text.
* **Short Text Sparsity:** Naive Bayes relies on word frequency. Short snippets like *"I'm a king"* lacked enough unique tokens for the model to distinguish between Jin's assertive tracks and Suga's hip-hop roots.

## 2. Optimization Phase: Data Balancing
To resolve the bias, we implemented **Stratified Sub-sampling**. 
* **Method:** We capped the maximum number of songs per member at 25.
* **Result:** This forced the model to learn the *unique stylistic markers* of members with smaller solo catalogs (like Jimin or V) rather than relying on label frequency.

## 3. The Final Architecture: Linear SVM + Character N-Grams
The breakthrough in accuracy came from two major architectural shifts:

### A. From Words to Character N-Grams
Instead of tokenizing by word (1-gram), we utilized **Character N-Grams (range 3-6)**.
- **Why?** This captures sub-word patterns, suffix usage, and rhythmic structures (e.g., the way a rapper might repeat certain syllable structures vs. a vocalist's elongated vowel patterns).

### B. Linear Support Vector Machine (LSVM)
We replaced MNB with a **Linear SVC** wrapped in a **Calibrated Classifier**.
- **Impact:** SVMs are "geometric" classifiers that find the optimal hyperplane between classes. In high-dimensional text space, this allowed for much sharper boundaries between members who share similar vocabulary but different "voices."

## 📊 Comparative Performance

| Version | Feature Set | Avg. Accuracy | Key Weakness |
| :--- | :--- | :--- | :--- |
| v1.0 | TF-IDF (Words) + Naive Bayes | 62% | Heavily biased toward RM/Suga |
| v2.0 | TF-IDF (N-Grams) + Balanced Data | 74% | Struggled with short snippets |
| **v3.0 (Final)** | **Char N-Grams + Linear SVM** | **82%** | **Optimized for all members** |
