# Predicting-Viewer-Engagement-in-OTT-Streaming-using-clustering-and-classification
# 🎬 OTT Viewer Dropoff & Retention  


This repository contains a complete machine learning pipeline for analyzing **OTT (Over-The-Top) viewer behavior**, segmenting episodes into **engagement clusters**, and predicting the engagement category of new episodes using supervised learning.

---

## 📌 Project Overview

The goal of this project is to:
1. **Identify distinct viewer engagement patterns** using unsupervised learning (clustering).
2. **Train a predictive model** that classifies new OTT episodes into engagement clusters based on behavioral and content attributes.
3. **Deploy the model** through an interactive interface for real-time predictions.

---

## 🧠 Project Objectives

- Analyze viewer interaction and drop-off behavior
- Engineer meaningful engagement and friction metrics
- Segment episodes into engagement-based clusters
- Predict engagement cluster for unseen episodes
- Enable real-world usage through a simple web interface

---

## 📂 Dataset Summary

- **File:** `ott_viewer_dropoff_retention_us_v1.0.csv`
- **Observations:** 33,171
- **Features:** 23
- **Missing Values:** None (0.0%)

### Key Feature Categories
**Identifiers & Metadata**
- `show_id`, `title`, `platform`, `genre`, `release_year`

**Viewer Behavior Metrics**
- `pause_count`, `rewind_count`, `skip_intro`
- `avg_watch_percentage`, `drop_off`, `drop_off_probability`

**Content Attributes**
- `episode_duration_min`, `pacing_score`, `hook_strength`
- `visual_intensity`, `cognitive_load`, `dialogue_density`
- `attention_required`, `night_watch_safe`, `retention_risk`

---

## 🛠️ Data Preprocessing & Feature Engineering

### Type Conversion
- `release_year` → integer  
- `avg_watch_percentage` → float  

### Binning / Discretization
Continuous variables were converted into ordered categories:

- **Pause Count:** `low_pause`, `medium_pause`, `high_pause`, `very_high_pause`
- **Rewind Count:** `low_rewind`, `medium_rewind`, `high_rewind`, `very_high_rewind`
- **Pacing Score:** `low_pacing`, `medium_pacing`, `high_pacing`, `very_high_pacing`
- **Hook Strength:** `weak_hook`, `moderate_hook`, `strong_hook`, `very_strong_hook`

### Engineered Features
New features created to better represent engagement dynamics:

- `content_age`
- `rewind_pause_ratio`
- `episode_progress`
- `engagement_score`
- `friction_score`
- `skip_rate`

### Encoding
- One-hot encoding applied to categorical features
- Final encoded dataset: **68 features**

---

## 🔍 Unsupervised Learning: Clustering

- **Scaling:** `StandardScaler`
- **Dimensionality Reduction:** PCA
- **Clustering Algorithm:** K-Means
- **Number of Clusters:** `5`

Each episode is assigned an **Engagement Cluster (0–4)** representing distinct viewer behavior patterns.

---

## 🤖 Supervised Learning: Classification

### Model
- **Algorithm:** K-Nearest Neighbors (KNN)
- **Neighbors:** `k = 3`

### Training Setup
- **Train/Test Split:** 80% / 20%
- **Random State:** 42

### Performance
- **Accuracy:** **82.26%**
- **Evaluation:** Confusion Matrix across 5 engagement clusters

---

## 🚀 Deployment & Prediction Interface

### Saved Assets
- Trained `KNN` model
- `StandardScaler`
- `PCA` transformer  
(All saved using `joblib`)

### Gradio Web Interface
An interactive interface allows users to predict engagement clusters for new episodes.

#### User Inputs (12 Features)
- `pacing_score`
- `hook_strength`
- `rewind_count`
- `pause_count`
- `skip_intro`
- `avg_watch_percentage`
- `cognitive_load`
- `platform`
- `genre`
- `dialogue_density`
- `attention_required`
- `release_year`

#### Prediction Flow
1. Recalculate engineered features
2. Apply scaler and PCA
3. Predict engagement cluster using trained KNN model

---

## 📦 Tech Stack

- Python
- Pandas, NumPy
- Scikit-learn
- PCA & K-Means
- Joblib
- Gradio
- Jupyter Notebook

---

## 📈 Results & Use Cases

- Identify high-risk content likely to experience viewer drop-off
- Optimize content pacing and structure
- Support data-driven content strategy decisions
- Enable real-time engagement prediction for new OTT episodes

---

## 📜 License

This project is for educational and research purposes.

---

⭐ *If you find this project useful, consider giving it a star!*
