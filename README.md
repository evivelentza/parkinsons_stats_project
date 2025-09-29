# Statistical Analysis of the Parkinson’s Voice Dataset  

## 📖 Project Overview  
This project applies a **5-step statistical analysis workflow** to the [UCI Parkinson’s Voice Dataset](https://archive.ics.uci.edu/ml/datasets/parkinsons).  
The dataset contains **22 voice features** extracted from sustained phonation recordings, along with a **status label** (1 = Parkinson’s Disease, 0 = healthy).  

The goal:  
- Explore how acoustic features differ between PD and controls  
- Identify **potential biomarkers** for diagnosis  
- Demonstrate statistical and machine learning techniques in a health data context  

---

## 🛠️ Workflow  

### 🔹 Step 1: Descriptive Statistics & Distribution Checks  
- Explored feature distributions (histograms, boxplots, QQ-plots).  
- Checked **normality (Shapiro–Wilk)** and **variance equality (Levene’s test)**.  
- Found that jitter/shimmer are highly skewed, HNR closer to normal.  

📌 Deliverable: Summary of which features are approximately normal vs. skewed.  

---

### 🔹 Step 2: Parametric vs Non-Parametric Testing  
- Compared PD vs. healthy for each feature.  
- Chose **Mann–Whitney U** for most (non-normal) features, Welch’s t-test for rare normal ones.  
- Applied **multiple testing correction** (Benjamini–Hochberg FDR).  

📌 Result: **Spread1, PPE, and MDVP:APQ** emerged as most significant (p_FDR < 1e-9).  

---

### 🔹 Step 3: Confidence Intervals & Hypothesis Testing  
- Computed **bootstrap 95% confidence intervals** for medians.  
- Confirmed significant differences (Mann–Whitney p-values).  
- Quantified effect sizes (rank-biserial correlations).  

📌 Example:  
- Spread1: Healthy median -6.83 vs PD -5.44, effect size 0.79 → **very strong difference**.  

---

### 🔹 Step 4: Effect Sizes, Errors & Power  
- Calculated **Cohen’s d** for top features (all > 0.9 → very large).  
- Ran **power analysis** (statsmodels):  
  - Only ~6–18 samples per group needed to detect these differences with 80% power.  
- Discussed **Type I (false positives)** and **Type II (false negatives)** in this context.  

📌 Conclusion: Dataset is more than sufficient to detect clinically meaningful differences.  

---

### 🔹 Step 5: Correlation & Regression  

- **Spearman correlation heatmap** → revealed redundancy (e.g., shimmer/APQ cluster, jitter family, Spread1 ≈ PPE).  
- **Simple regressions** (e.g., PPE ~ Spread1) showed near-linear dependence (R² ≈ 0.95).  
- **Logistic regression with VIF pruning**: Spread1, PPE, APQ remain robust predictors.  
- **Regularization (L1/L2)** confirmed that a small subset of features suffices for high predictive accuracy (AUC ≈ 0.95).  

📌 Deliverable: Odds ratios, ROC curves, and regularized feature selection results.  

---

## 🔑 Key Insights  
- PD patients show **greater voice irregularity** (jitter, shimmer, APQ) and **nonlinear frequency variation** (Spread1, PPE).  
- A **compact model with 3–4 features** achieves excellent discrimination (AUC ~0.95).  
- Confirms known biomarkers while showcasing a reproducible, researcher-style workflow.  

---

## 📂 Repo Structure  
parkinsons_stats_project/
│
├── data/ # Parkinson’s dataset (.csv, .names)
├── notebooks/ # Jupyter notebook
├── summary.csv # Final statistical summary tables
└── README.md # This file

---

## 🧰 Methods & Tools  
- **Python**: pandas, numpy, scipy, statsmodels, sklearn, seaborn, matplotlib  
- **Statistics**: Shapiro–Wilk, Levene’s test, Mann–Whitney U, bootstrap CIs, Cohen’s d, power analysis  
- **ML**: Logistic regression, L1/L2 regularization, ROC/AUC  

---

## 📜 References  
- Little MA, McSharry PE, Roberts SJ, Costello DAE, Moroz IM.  
  *Exploiting Nonlinear Recurrence and Fractal Scaling Properties for Voice Disorder Detection*.  
  BioMedical Engineering OnLine 2007, 6:23.  

- UCI Machine Learning Repository: [Parkinson’s Dataset](https://archive.ics.uci.edu/ml/datasets/parkinsons)  

---

This project demonstrates how to move from **EDA → statistical testing → effect size → regression modeling** in a **healthcare context**.  
It can serve as a **template for biomarker discovery projects** in biotech, neuroscience, and beyond.  
