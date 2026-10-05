# Rainfall Prediction Classifier

<div align="center">

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Manuel-Cavina/Rainfall-prediction/blob/main/Rainfall%20Prediction%20Classifier.ipynb)
[![Python](https://img.shields.io/badge/Python-3.x-173B57?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F3E9D2?style=flat-square&logo=scikitlearn&logoColor=173B57)](https://scikit-learn.org/)

**A time-aware Machine Learning project that predicts whether it will rain the following day in the Melbourne area.**

</div>

---

## Project Overview

This project uses historical weather observations to answer a binary classification question:

> **Will it rain tomorrow in the Melbourne area?**

It was developed as the final project for IBM's **Machine Learning with Python** course and later expanded with clearer preprocessing, chronological validation, model comparison, probability evaluation and prediction traceability.

The analysis covers observations from three Australian weather stations:

- Melbourne
- Melbourne Airport
- Watsonia

The target variable is **RainTomorrow**:

- **Yes:** rain was recorded on the following day.
- **No:** rain was not recorded on the following day.

---

## Why This Project Matters

Rainfall prediction is not only a classification problem. It also requires careful handling of time, missing weather measurements and imbalanced outcomes.

A useful solution must avoid learning from future information, report more than accuracy and preserve enough traceability to understand how each prediction was produced.

---

## Machine Learning Workflow

1. **Data exploration** — inspect variables, locations, target distribution and missing values.
2. **Data cleaning** — parse dates, validate labels and exclude unusable records while preserving exclusion reasons.
3. **Chronological split** — train on earlier observations and test on later observations to simulate future prediction.
4. **Feature engineering** — derive Southern Hemisphere seasons from observation dates.
5. **Preprocessing pipeline** — impute missing values, scale numerical variables and encode categorical features.
6. **Baseline model** — compare trained models against a classifier that always predicts the majority class.
7. **Time-aware validation** — evaluate candidates with chronological cross-validation instead of random folds.
8. **Model comparison** — tune and compare Logistic Regression and Random Forest.
9. **Final evaluation** — measure classification quality, probability ranking and calibration on an untouched test period.
10. **Prediction audit** — retain dates, locations, actual outcomes, probabilities and predicted classes for traceability.

---

## Data Split

The dataset was separated chronologically:

| Partition | Rows | Observation period |
| --- | ---: | --- |
| Training | 6,749 | July 2008 — September 2015 |
| Boundary buffer | 2 | September 25, 2015 |
| Test | 1,692 | September 2015 — June 2017 |

The boundary buffer prevents an observation from the training period from using a target that belongs to the test period.

---

## Model Selection

Model selection was performed only with training-period data using three chronological validation folds.

| Model | CV Average Precision | CV F1 | CV Accuracy |
| --- | ---: | ---: | ---: |
| Logistic Regression | 0.703 | 0.582 | 0.824 |
| Random Forest | 0.675 | 0.521 | 0.813 |

**Logistic Regression** was selected before evaluating the final test period because it achieved the strongest validation results.

---

## Test Results

| Model | Accuracy | Rain Precision | Rain Recall | Rain F1 | Average Precision | ROC AUC |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| Majority baseline | 0.763 | 0.000 | 0.000 | 0.000 | 0.237 | 0.500 |
| **Logistic Regression** | **0.828** | **0.683** | **0.511** | **0.585** | **0.668** | **0.850** |
| Random Forest | 0.827 | 0.723 | 0.436 | 0.544 | 0.672 | 0.856 |

The selected Logistic Regression model correctly classified approximately **82.8%** of the test observations.

Accuracy alone is not sufficient because the majority baseline already reaches 76.3% by predicting **No rain** every time. The selected model provides meaningful rain detection, reaching 68.3% precision and 51.1% recall for the rain class.

---

## Main Technologies

- **Python**
- **pandas** and **NumPy**
- **Matplotlib** and **seaborn**
- **scikit-learn**
- **Google Colab** and **Jupyter Notebook**

---

## Repository Contents

| File | Purpose |
| --- | --- |
| [Rainfall Prediction Classifier.ipynb](./Rainfall%20Prediction%20Classifier.ipynb) | Complete analysis, preprocessing, model training, evaluation and exported results. |
| [Certificate.pdf](./Certificate.pdf) | IBM Machine Learning with Python course certificate. |
| [README.md](./README.md) | Project overview, methodology and results. |

---

## Run the Project

### Google Colab

Use the **Open in Colab** button at the top of this README and run the notebook cells in order.

The notebook downloads the weather dataset from its original source, so internet access is required.

### Local Environment

Clone the repository:

```bash
git clone https://github.com/Manuel-Cavina/Rainfall-prediction.git
cd Rainfall-prediction
```

Install the required libraries:

```bash
python -m pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

Then open `Rainfall Prediction Classifier.ipynb` in VS Code or Jupyter and run the cells in order.

The final Colab download cell can be skipped when running locally.

---

## Limitations

- The project uses historical observations from only three stations in the Melbourne area.
- The positive rain class is less frequent than the no-rain class.
- The model detects approximately half of the rain events at the default decision threshold.
- These results do not guarantee the same performance on future periods, other regions or changing climate conditions.
- This is an educational Machine Learning project and not an operational weather forecasting service.

---

## Sources

- [IBM Machine Learning with Python — Coursera](https://www.coursera.org/learn/machine-learning-with-python)
- [Rain in Australia dataset — Kaggle](https://www.kaggle.com/datasets/jsphyg/weather-dataset-rattle-package)
