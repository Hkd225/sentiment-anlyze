# Sentiment Analysis Indonesian Adjectives (IndoBERT)

This project performs **sentiment analysis (positive, neutral, negative)**  
on **Indonesian adjectives (kata sifat)** using **IndoBERT** with a weighted-loss
training strategy to handle class imbalance.

The dataset is sourced from Kaggle and sentiment labels are generated using
a **heuristic keyword-based labeling approach**, then refined through
fine-tuning a transformer model.

---

## Dataset
- **Source**: Kaggle  
- **Link**: https://www.kaggle.com/datasets/linkgish/indonesian-adjective-sentiment-kata-sifat  
- **Description**:  
  A collection of Indonesian adjectives with explanations, used to infer
  sentiment polarity (positive, neutral, negative).

> ⚠️ Dataset is **not stored in this repository**.  
> It is downloaded dynamically using the Kaggle API.

---

## Model
- **Base Model**: `indolem/indobert-base-uncased`
- **Architecture**: Transformer-based sequence classification
- **Labels**:
  - 0 → Negative  
  - 1 → Neutral  
  - 2 → Positive
- **Loss Function**: CrossEntropyLoss with **class weighting**
- **Early Stopping**: Enabled

---

## Training Details
- **Epochs**: 12
- **Learning Rate**: 1e-5
- **Batch Size**:
  - Train: 4
  - Evaluation: 8
- **Max Sequence Length**: 128
- **Evaluation Metrics**:
  - Accuracy
  - Weighted F1-score
- **Device**:
  - CUDA (GPU) if available
  - CPU fallback

---

## Features
- Heuristic sentiment labeling based on explanation keywords
- Class imbalance handling with weighted loss
- Train / Validation / Test split with stratification
- Model export for:
  - Reuse
  - Website / API integration (JSON output)
- Inference class for real-time prediction

---

## Tech Stack
- Python
- PyTorch
- HuggingFace Transformers
- HuggingFace Datasets
- Scikit-learn
- Pandas & NumPy

---

## Example Prediction
```text
Kata  : bagus
Makna : sangat baik dan memuaskan
Hasil : POSITIVE (confidence ~0.9)
```
Author
Muhammad Auffa Hakim Aditya

Computer Science Student – UPN "Veteran" Jawa Timur
