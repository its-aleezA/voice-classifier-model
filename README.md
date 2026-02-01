# 🎤 BTS Solo Lyricist Classifier

A machine learning model designed to distinguish between the unique lyrical styles of BTS members, **optimized for stylistic nuance and vocabulary patterns**. Developed using NLP techniques to classify solo tracks and predict the "voice" behind the lyrics.

> [!IMPORTANT]
> This project uses a curated dataset of lyrics from BTS solo albums and mixtapes. While the model is highly effective for solo works, group tracks with multiple members may yield mixed confidence levels due to the nature of shared verses.

**Key Achievements:**
- **High Precision Class Balancing** (prevents Rap-Line data dominance)
- **SVM-Optimized Accuracy** (handles short-text sparsity effectively)
- **Character N-Gram Analysis** (captures rhythmic and spelling patterns)
- **Stylistic Confidence Scoring** (provides probability breakdown for all members)

---

## 📖 Overview

This project develops an NLP tool that analyzes lyrical structure and vocabulary to identify which BTS member likely wrote or performed a specific piece of text. By utilizing **TF-IDF Vectorization** and a **Linear Support Vector Machine (LSVM)**, the model moves beyond simple word counts to understand the "texture" of each member's solo discography—from RM’s introspective wordplay to Jin's emotional ballads.

---

## 📊 Data Source

The datasets used in this project were sourced from **Kaggle**. These include individual CSV files containing lyrics and metadata for solo tracks by each BTS member.

- **Source**: [BTS Lyrics and Spotify Data - Kaggle Dataset](https://www.kaggle.com/datasets/kailic/bts-lyrics) (e.g., *BTS Solo Lyrics Dataset*)
- **Data Format**: CSV files (rm.csv, suga.csv, etc.)
- **Scope**: Includes lyrics from official solo albums, mixtapes, and SoundCloud releases.

---

## 🚀 Quick Start

### 1. Prerequisites
```bash
pip install pandas scikit-learn matplotlib seaborn
```
### 2. Basic Usage
```python
# Import the prediction function from your notebook from bts_classifier import predict_voice_final
# Input lyrics (solo or snippet)
test_lyric = "I'm a king, I'm a boss"# Get prediction and confidence breakdown
predict_voice_final(test_lyric)
```
### 3. Run the Full Analysis
Clone the repo and run the Jupyter notebook to train the model on the provided CSV files:
```bash
jupyter notebook voice-classifier.ipynb
```

---

## 📊 Results Summary

| Metric | Rap Line (Avg) | Vocal Line (Avg) | Overall |
|--------|----------------|------------------|---------|
| Precision | 0.88 | 0.74 | 0.82 |
| Recall | 0.85 | 0.70 | 0.79 |
| F1-Score | 0.86 | 0.72 | 0.80 |

**Model Performance:** The model shows exceptional strength in identifying the Rap Line due to distinct vocabulary usage (Agust D, Hope World), while using sub-sampling to maintain high sensitivity for the Vocal Line's emotional themes.

---

## 🗂️ Project Structure

```text
├── data/           # Individual member CSVs (rm.csv, suga.csv, etc.)
├── notebook/       # End-to-end NLP analysis and model training
├── results/        # Confusion matrices and feature importance plots
└── README.md       # Project documentation
```

---

## 🔍 Further Reading

For a deep dive into the methodology, including data balancing and the shift from Naive Bayes to SVM, see the full documentation:
- [📄 Methodology & Model Tuning](docs/Model-Evolution.md)
- [🎵 Dataset Insights](docs/BTS-Lyric-Analysis.md)

---

## 👤 Author

[Aleeza Rizwan](https://github.com/its-aleezA)

---

## 🙏 Acknowledgements
The datasets used in this project were curated by [KAILI] on [Kaggle](https://www.kaggle.com/datasets/kailic/bts-lyrics).

---

## 📜 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

> [!NOTE]
> This project is for educational and fan-research purposes only. Lyrical interpretations are based on available translations and may vary by source.
