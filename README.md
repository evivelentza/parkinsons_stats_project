# 🧠 Parkinson's Disease Statistics Project

## 📖 Overview
This project performs a statistical analysis of the [UCI Parkinson's dataset](https://archive.ics.uci.edu/ml/datasets/parkinsons).  
The goal is to explore differences in **voice features** between Parkinson's patients and healthy controls,  
using descriptive statistics, hypothesis testing, and regression analysis.  

The analysis focuses on **clinically interpretable voice measures**—such as jitter, shimmer, and harmonic-to-noise ratio (HNR)—that are commonly associated with dysphonia in Parkinson’s disease.

---

## 📊 Dataset
- **Source:** UCI Machine Learning Repository  
- **Citation:**  
  If you use this dataset, please cite:  
  *Little MA, McSharry PE, Roberts SJ, Costello DAE, Moroz IM (2007).*  
  *"Exploiting Nonlinear Recurrence and Fractal Scaling Properties for Voice Disorder Detection."*  
  *BioMedical Engineering OnLine, 6:23 (26 June 2007).*  

- **File:** `parkinsons.csv`  
- **Samples:** 195 voice recordings (31 subjects, 23 with Parkinson’s disease)  
- **Features:** 22 biomedical voice measures (e.g., jitter, shimmer, HNR)  
- **Target:** `status` (1 = Parkinson’s, 0 = Healthy)

---

## ⚙️ Methods
- **Descriptive Statistics**: mean, SD, median, IQR  
- **Hypothesis Testing**: independent-samples t-tests, Cohen’s d effect sizes  
- **Correlation Analysis**: pairwise feature correlations  
- **Visualization**: histograms, boxplots, scatterplots (status split)  
- **Regression (future extension)**: exploring logistic regression and feature importance  

---

## 🔬 Clinically Relevant Features
- **MDVP:Fo(Hz) – Fundamental Frequency (Pitch)**  
  Baseline pitch of the voice. In PD, pitch may show reduced range or higher variability, but overlaps strongly with healthy voices. Useful as a context feature when paired with HNR.  

- **MDVP:Jitter(%) – Frequency Instability**  
  High jitter = irregular vocal fold vibration. PD patients often show **higher jitter** due to tremor and instability.  

- **MDVP:Shimmer – Amplitude Instability**  
  High shimmer = uneven loudness in the voice. PD patients often show **increased shimmer**, another sign of dysphonia.  

- **HNR (Harmonic-to-Noise Ratio) – Voice Noisiness**  
  Lower HNR = noisier, breathier voice. PD patients tend to have **significantly lower HNR**, making it a strong, clinically interpretable biomarker.  

---

## 🔑 Key Findings
- **PD patients show increased voice instability**:  
  Higher values of **jitter** (frequency variation) and **shimmer** (amplitude variation) compared to healthy controls.  

- **PD patients show reduced voice quality**:  
  Lower **Harmonic-to-Noise Ratio (HNR)**, indicating noisier, breathier voices.  

- **Fundamental frequency (Fo)** alone is less discriminative:  
  While pitch overlaps between groups, when paired with HNR it provides useful context for classification.  

- **Clinical interpretation**:  
  Together, these features provide **clinically interpretable biomarkers** that can support **machine learning models** for Parkinson’s detection.  

---

## ✅ Requirements
See `requirements.txt` for the full list of dependencies. Typical stack:  
```bash
pandas
numpy
matplotlib
scipy
