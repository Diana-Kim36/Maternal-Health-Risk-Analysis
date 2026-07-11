# Maternal Health Risk Analysis

## Machine Learning for Early Identification of High-Risk Pregnancies

This project uses machine learning to classify maternal health records into **low-risk, mid-risk, and high-risk pregnancy categories** using routine clinical measurements.

> **Clinical disclaimer:** This project is intended for educational and analytical purposes only. The model is a decision-support prototype and must not replace professional medical judgment, diagnosis, or treatment.

---

## Project Highlights

| Metric | Result |
|---|---:|
| Dataset size | 1,014 pregnancies |
| Clinical predictors | 6 |
| Model | Random Forest Classifier |
| Number of trees | 200 |
| Cross-validated accuracy | 85.2% ± 2.0% |
| High-risk recall | 96.3% |
| High-risk precision | 93% |
| Primary risk factor | Blood Sugar |
| Blood Sugar importance | 36.4% |

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Dataset Overview](#2-dataset-overview)
3. [Exploratory Data Analysis](#3-exploratory-data-analysis)
4. [Key Visualizations](#4-key-visualizations)
5. [Feature Importance](#5-feature-importance)
6. [Model Performance](#6-model-performance)
7. [Key Findings](#7-key-findings)
8. [Recommendations](#8-recommendations)
9. [Limitations](#9-limitations)
10. [Conclusion](#10-conclusion)
11. [Suggested Repository Structure](#11-suggested-repository-structure)

---

## 1. Executive Summary

This analysis develops a machine learning model to identify pregnancies at high risk of complications using six clinical features:

- Age
- Systolic blood pressure
- Diastolic blood pressure
- Blood sugar
- Body temperature
- Heart rate

A Random Forest classifier trained on 1,014 maternal health records achieved **85.2% cross-validated accuracy** and identified **96.3% of high-risk cases**.

Blood sugar was the most influential predictor, accounting for **36.4% of model importance**. It was followed by systolic blood pressure, maternal age, and diastolic blood pressure.

The results demonstrate how predictive analytics can support early maternal-risk screening and help healthcare teams prioritize patients who may require closer monitoring.

---

## 2. Dataset Overview

The dataset contains **1,014 complete maternal health records** with six clinical predictors and one target variable.

### Clinical Features

| Feature | Range | Mean | Standard Deviation |
|---|---:|---:|---:|
| Age | 10–70 years | 29.9 | 13.5 |
| Systolic Blood Pressure | 70–160 mmHg | 113.2 | 18.4 |
| Diastolic Blood Pressure | 49–100 mmHg | 76.5 | 13.3 |
| Blood Sugar | 6.0–19.0 mmol/L | 8.7 | 3.6 |
| Body Temperature | 98.0–103.0°F | 98.7 | 1.4 |
| Heart Rate | 7–90 bpm | 74.3 | 8.1 |

### Risk-Level Distribution

| Risk Level | Cases | Percentage |
|---|---:|---:|
| Low Risk | 406 | 40.0% |
| Mid Risk | 336 | 33.1% |
| High Risk | 272 | 26.8% |

The dataset contains no missing values. Its target classes are reasonably balanced, with a slight concentration of low-risk pregnancies.

---

## 3. Exploratory Data Analysis

A Kruskal-Wallis non-parametric test showed statistically significant differences across the three risk groups for all six clinical features.

### Effect Sizes

| Feature | Effect Size (η²) | Interpretation | Key Finding |
|---|---:|---|---|
| Blood Sugar | 0.2985 | Large | Strongest risk differentiator |
| Systolic BP | 0.1623 | Medium | Second most important factor |
| Diastolic BP | 0.1303 | Medium | Complements systolic BP |
| Age | 0.0956 | Small–Medium | Moderate contribution |
| Heart Rate | 0.0351 | Small | Weak but significant effect |
| Body Temperature | 0.0306 | Small | Lowest differentiation |

### High-Risk vs. Low-Risk Clinical Profiles

| Metric | High Risk | Low Risk | Difference |
|---|---:|---:|---:|
| Age | 36.2 years | 26.9 years | +9.3 years |
| Systolic BP | 124.2 mmHg | 105.9 mmHg | +18.3 mmHg |
| Diastolic BP | 85.1 mmHg | 72.5 mmHg | +12.6 mmHg |
| Blood Sugar | 12.1 mmol/L | 7.2 mmol/L | +4.9 mmol/L |
| Body Temperature | 98.9°F | 98.4°F | +0.5°F |
| Heart Rate | 76.7 bpm | 72.8 bpm | +3.9 bpm |

High-risk pregnancies were associated with higher maternal age, elevated blood pressure, and substantially higher blood sugar.

---

## 4. Key Visualizations

The project includes the following recommended visualizations:

- Correlation matrix heatmap
- Blood sugar distribution by risk level
- Feature importance bar chart
- Confusion matrix
- Risk-level distribution chart
- Clinical profile comparison by risk category

### Correlation Findings

Blood sugar showed the strongest positive relationship with maternal risk.

| Feature | Correlation With Risk |
|---|---:|
| Blood Sugar | 0.57 |
| Systolic BP | 0.40 |
| Diastolic BP | 0.35 |

Systolic and diastolic blood pressure were also strongly correlated with one another, with a correlation of approximately **0.79**.

### Adding Images to GitHub

Save your charts inside an `images` folder and insert them into this README using:

```markdown
![Correlation Matrix](images/correlation_matrix.png)
![Blood Sugar Distribution](images/blood_sugar_distribution.png)
![Feature Importance](images/feature_importance.png)
![Confusion Matrix](images/confusion_matrix.png)
```

---

## 5. Feature Importance

The Random Forest model used 200 decision trees.

| Rank | Feature | Importance Score | Percentage |
|---:|---|---:|---:|
| 1 | Blood Sugar | 0.364 | 36.4% |
| 2 | Systolic BP | 0.182 | 18.2% |
| 3 | Age | 0.162 | 16.2% |
| 4 | Diastolic BP | 0.123 | 12.3% |
| 5 | Heart Rate | 0.105 | 10.5% |
| 6 | Body Temperature | 0.064 | 6.4% |

### Interpretation

Blood sugar was the most important model feature and contributed more than twice as much predictive importance as systolic blood pressure.

Systolic and diastolic blood pressure together accounted for **30.5%** of model importance, highlighting the relevance of hypertension-related indicators.

Maternal age contributed **16.2%**, while body temperature had the lowest predictive importance.

---

## 6. Model Performance

### Model Configuration

- Algorithm: Random Forest Classifier
- Number of trees: 200
- Dataset size: 1,014 records
- Validation method: Five-fold cross-validation
- Mean cross-validated accuracy: 85.2%
- Standard deviation: ±2.0%
- Accuracy range across folds: 82.3%–87.6%

### Per-Class Performance

| Risk Category | Precision | Recall | F1-Score | Support |
|---|---:|---:|---:|---:|
| High Risk | 0.93 | 0.96 | 0.95 | 272 |
| Low Risk | 0.96 | 0.90 | 0.93 | 406 |
| Mid Risk | 0.88 | 0.92 | 0.90 | 336 |
| Overall | 0.92 | 0.92 | 0.92 | 1,014 |

The most clinically important result is the model's **96.3% recall for high-risk pregnancies**. This means the model correctly identified approximately 96 out of every 100 high-risk cases in the analyzed dataset.

### Confusion Matrix

| Actual \ Predicted | High Risk | Low Risk | Mid Risk |
|---|---:|---:|---:|
| High Risk | 262 | 4 | 6 |
| Low Risk | 5 | 364 | 37 |
| Mid Risk | 14 | 12 | 310 |

### Misclassification Patterns

| Error Type | Count | Percentage | Interpretation |
|---|---:|---:|---|
| High Risk predicted as Low Risk | 4 | 1.5% | Most concerning false negatives |
| High Risk predicted as Mid Risk | 6 | 2.2% | Still likely to receive review |
| Low Risk predicted as Mid Risk | 37 | 9.1% | May create extra evaluation |
| Mid Risk predicted as High Risk | 14 | 4.2% | Conservative over-flagging |
| Low Risk predicted as High Risk | 5 | 1.2% | False alarm |
| Mid Risk predicted as Low Risk | 12 | 3.6% | Potential under-identification |

The model performed especially well when identifying high-risk pregnancies, although a small number of high-risk cases were incorrectly classified as low risk.

---

## 7. Key Findings

### 7.1 Blood Sugar Was the Primary Risk Indicator

Blood sugar had:

- The largest statistical effect size: **η² = 0.2985**
- The highest feature importance: **36.4%**
- A high-risk mean of **12.1 mmol/L**
- A low-risk mean of **7.2 mmol/L**

Low-risk pregnancies were concentrated around 6–8 mmol/L, while many high-risk cases occurred between 10 and 19 mmol/L.

### 7.2 Blood Pressure Was a Major Risk Domain

Systolic and diastolic blood pressure together accounted for approximately **30.5%** of model importance.

High-risk pregnancies had average blood pressure values of:

- Systolic BP: 124.2 mmHg
- Diastolic BP: 85.1 mmHg

Low-risk pregnancies had average values of:

- Systolic BP: 105.9 mmHg
- Diastolic BP: 72.5 mmHg

### 7.3 Advanced Maternal Age Increased Risk

The average age of high-risk patients was **36.2 years**, compared with **26.9 years** for low-risk patients.

Maternal age accounted for **16.2%** of model importance.

### 7.4 Multiple Elevated Factors Increased Concern

The model results suggest that pregnancies involving a combination of elevated blood sugar, elevated blood pressure, and advanced maternal age should receive closer clinical assessment.

---

## 8. Recommendations

These recommendations are analytical interpretations and should only be implemented under qualified clinical leadership.

### Metabolic Risk Screening

- Prioritize blood sugar evaluation during prenatal risk assessment.
- Closely review patients with abnormal or elevated glucose measurements.
- Repeat testing when clinically appropriate.
- Use confirmed clinical guidelines rather than model-derived thresholds alone.

### Blood Pressure Monitoring

- Measure blood pressure consistently during prenatal visits.
- Investigate persistent or clinically significant elevations.
- Assess for other warning signs of hypertensive pregnancy disorders.
- Follow current obstetric guidelines for treatment and referral.

### Risk Stratification

- Use the model as a decision-support tool.
- Reassess risk as pregnancy progresses.
- Refer higher-risk patients for specialist review when clinically indicated.
- Do not use a model prediction as the sole basis for diagnosis or treatment.

### Age-Based Monitoring

- Consider enhanced monitoring for pregnancies at advanced maternal age.
- Evaluate age together with blood sugar, blood pressure, medical history, and other clinical factors.

### Implementation Strategy

A future version of the project could be deployed as:

- A Streamlit web application
- A Flask or FastAPI service
- A mobile screening prototype
- An electronic health record decision-support module
- A Power BI dashboard with risk indicators

Before real-world deployment, the model would require external validation, clinical review, privacy protections, fairness testing, and regulatory assessment.

---

## 9. Limitations

### Cross-Sectional Design

The dataset captures a limited clinical snapshot and does not model changes across pregnancy trimesters.

### Limited Clinical Features

The dataset does not include several potentially important predictors, such as:

- Obstetric history
- Parity
- Previous pregnancy complications
- Medical comorbidities
- Medication use
- Smoking and substance use
- Diet and exercise
- Socioeconomic factors
- Access to prenatal care
- Multiple gestation
- Confirmed pregnancy outcomes

### Unknown Sampling Process

The dataset does not provide sufficient information about sampling methods, clinical setting, or population representativeness.

### Risk Labels Are Not Direct Outcomes

The target variable represents assigned risk categories rather than confirmed outcomes such as preeclampsia, preterm birth, cesarean delivery, or neonatal complications.

### Static Prediction

The model generates a single classification and does not account for changing measurements over time.

### Generalizability

The model should not be assumed to perform equally well across hospitals, countries, racial or ethnic groups, or different socioeconomic populations.

### Model Interpretability

Random Forest models provide feature importance but do not always offer simple, patient-level explanations. Future work could include SHAP values or comparison with an interpretable logistic regression model.

### In-Sample vs. Cross-Validated Results

The 92% overall classification metrics are in-sample results, while the 85.2% figure is the more conservative cross-validated accuracy estimate. Cross-validated or external-test results should be prioritized when discussing expected generalization.

---

## 10. Conclusion

This project demonstrates that six routinely collected clinical measurements can be used to build a machine learning model for maternal health risk classification.

The Random Forest model achieved:

- **85.2% cross-validated accuracy**
- **96.3% recall for high-risk pregnancies**
- **93% precision for high-risk pregnancies**

Blood sugar was the most influential predictor, followed by blood pressure and maternal age.

The results support the potential value of predictive analytics in prenatal risk screening. However, the model must be treated as an educational decision-support prototype rather than a clinically validated diagnostic tool.

Future work should include:

- External validation
- Longitudinal pregnancy data
- Confirmed maternal and neonatal outcomes
- Additional clinical and socioeconomic predictors
- Fairness and bias evaluation
- Patient-level model explanations
- Prospective clinical testing

---

## 11. Suggested Repository Structure

```text
maternal-health-risk-analysis/
│
├── README.md
├── data/
│   └── maternal_health_risk_data.csv
├── notebooks/
│   └── maternal_health_analysis.ipynb
├── src/
│   ├── data_preprocessing.py
│   ├── train_model.py
│   └── evaluate_model.py
├── images/
│   ├── correlation_matrix.png
│   ├── blood_sugar_distribution.png
│   ├── feature_importance.png
│   └── confusion_matrix.png
├── model/
│   └── random_forest_model.pkl
├── requirements.txt
└── LICENSE
```

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook
- Random Forest Classification
- Kruskal-Wallis Statistical Testing

---

## Example Installation

```bash
git clone https://github.com/your-username/maternal-health-risk-analysis.git
cd maternal-health-risk-analysis
pip install -r requirements.txt
```

---

## Example Usage

```bash
jupyter notebook notebooks/maternal_health_analysis.ipynb
```

---

## Author

**Diana Kimanzi**

Master of Science in Business Analytics  
Data Analytics | Machine Learning | Healthcare Analytics

---

## License

This project is available for educational and portfolio purposes. Add a suitable open-source license, such as the MIT License, if you intend to allow reuse.
