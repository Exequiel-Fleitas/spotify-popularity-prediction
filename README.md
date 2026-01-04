# Predicting Spotify Song Popularity Using Audio Features

## Overview
This project investigates whether a song’s popularity can be predicted using **Spotify audio features alone**. Using data collected from Spotify’s API, several machine learning models were trained to predict track popularity based only on measurable audio characteristics such as loudness, energy, tempo, and danceability.

The goal is to understand:
- How much of song popularity can be explained by sound alone
- Which audio features contribute most to popularity
- Why nonlinear models outperform linear approaches in this context

---

## Dataset
The dataset consists of **4,831 tracks**, compiled from two sources:
- High-popularity tracks
- Low-popularity tracks

Each track includes:
- **Audio features** (Spotify audio analysis)
- **Descriptive metadata** (artist, playlist, album info)
- **Track popularity score** (0–100)

Only **audio features** were used for modeling to avoid data leakage.

### Audio Features Used
- Energy  
- Loudness  
- Danceability  
- Tempo  
- Valence  
- Speechiness  
- Instrumentalness  
- Acousticness  
- Liveness  
- Duration (ms)  
- Key  
- Mode  

---

## Methods

### Problem Type
- **Supervised regression**
- Target variable: `track_popularity`

### Models Trained
- Baseline (mean predictor)
- Linear Regression
- Random Forest Regressor
- Gradient Boosting Regressor

### Evaluation Metrics
- **RMSE** (Root Mean Squared Error)
- **R²** (Variance explained)

---

## Results

| Model | RMSE | R² |
|------|------|----|
| Random Forest | **16.80** | **0.26** |
| Gradient Boosting | 17.67 | 0.18 |
| Linear Regression | 18.67 | 0.09 |
| Baseline | 19.56 | -0.00 |

**Key Findings**
- Audio features contain meaningful predictive signal
- Nonlinear models significantly outperform linear regression
- Approximately **26% of popularity variance** can be explained by audio features alone

---

## What Makes a Song Popular?

### Feature Importance (Random Forest)
The most influential audio features were:
1. Loudness
2. Track duration
3. Instrumentalness (lower is better)
4. Energy
5. Acousticness

Traditional musical attributes such as **key and mode** had minimal impact.

---

## Model Explainability (SHAP)
SHAP analysis was used to interpret the Random Forest model:
- Loudness strongly increases predicted popularity beyond a threshold
- Loudness is most effective when paired with high energy
- High instrumentalness consistently decreases popularity
- Effects are **nonlinear and interactive**

These insights explain why tree-based models outperform linear regression.

---

## Conclusion
Song popularity can be **partially predicted** using Spotify audio features alone. Production-related attributes such as loudness and energy play a dominant role, while musical key and mode contribute little. However, most popularity variance remains unexplained, highlighting the importance of non-audio factors such as artist recognition, playlist placement, marketing, and cultural trends.

---

## Technologies Used
- Python
- pandas, NumPy
- scikit-learn
- SHAP
- matplotlib

---

## Future Work
- Incorporate genre and playlist metadata
- Perform binary classification (popular vs non-popular)
- Add statistical significance testing
- Explore temporal effects using release dates

---

## Author
Exequiel Fleitas  
Data Science & Music  
Southern Methodist University
