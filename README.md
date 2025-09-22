# Parkinson's Disease Statistics Project

## 📖 Overview
This project performs a statistical analysis of the [UCI Parkinson's dataset](https://archive.ics.uci.edu/ml/datasets/parkinsons).  
The goal is to explore differences in voice features between Parkinson's patients and healthy controls,  
using descriptive statistics, hypothesis testing, and regression analysis.

## 📊 Dataset
- **Source:** UCI Machine Learning Repository
- **File:** `parkinsons.csv`
- **Features:** 22 voice measures (jitter, shimmer, HNR, etc.)
- **Target:** `status` (1 = Parkinson’s, 0 = Healthy)

## ⚙️ Methods
- Descriptive statistics (mean, SD, median)
- Hypothesis testing (t-tests, correlations, ANOVA)
- Simple and multiple regression models
- Data visualization with matplotlib & seaborn

## ✅ Requirements
See `requirements.txt` for the full list of dependencies.

## ▶️ How to Run
1. Clone this repo  
2. Create a virtual environment and install dependencies:  
   ```bash
   pip install -r requirements.txt



MDVP:Fo(Hz) – fundamental frequency (pitch)

Baseline pitch of the voice.

In PD, pitch may be more variable or reduced range, but it overlaps a lot with healthy voices (not a strong single marker).

Useful as a context feature when paired with HNR.

MDVP:Jitter(%) – frequency instability

High jitter = irregular vocal fold vibration.

PD patients often show higher jitter due to tremor and instability.

Clinically important marker.

MDVP:Shimmer – amplitude instability

High shimmer = uneven loudness in the voice.

PD patients often show increased shimmer, another sign of dysphonia.

HNR (Harmonic-to-Noise Ratio) – voice noisiness

Lower HNR = noisier, breathier voice.

PD patients tend to have significantly lower HNR compared to healthy controls.

Strong, clinically interpretable biomarker.
