# Student Employability Classification

Vortex Tech AI & ML Internship 2026 — Week 2

## Overview

A binary classification project predicting whether a Pakistani university
student is likely to get hired (`likely_to_get_hired`: Yes/No), built on top
of the cleaned dataset produced in the Week 1 project
(`vortextech-aiml-week1`). Two models are trained and compared: Logistic
Regression and a Decision Tree, evaluated with accuracy, precision, recall,
and F1-score.

## Dataset

`pk_student_employability_cleaned.csv` — 47,839 cleaned student records, 49
columns, produced by the Week 1 data cleaning notebook (missing CGPA/
attendance rows dropped, skill and activity columns filled based on their
likely meaning, duplicates removed).

**Class imbalance:** the target is heavily imbalanced, about 96% Yes and 4%
No. This is treated as a deliberate part of the analysis rather than an
error — see Interpretation below.

## Files

- `student_employability_classification1.ipynb` — main classification
  notebook, every code cell preceded by a titled markdown description
- `pk_student_employability_cleaned.csv` — cleaned dataset used by the
  notebook
- `Week2_Classification_Model_Full_Guide.txt` — step-by-step explanation of
  every code cell, including the reasoning behind feature selection and
  leakage decisions
- `requirements.txt` — Python libraries required to run the notebook

## What the notebook covers

- Loading the cleaned dataset and inspecting the target's class balance
- Creating a numeric target column (1 = Yes, 0 = No)
- Feature selection: excluding `student_id` (identifier), and two data
  leakage risks, `employability_status` and `job_readiness_score`, both of
  which are strongly correlated with the target and would let the model
  appear to perform well without learning genuine patterns
- One-hot encoding categorical features
- An 80/20 train-test split, stratified to preserve the class imbalance
  ratio in both sets
- Training a Logistic Regression model (with feature scaling via a pipeline)
- Evaluating with accuracy, precision, recall, and F1-score, for both the
  majority (Yes) and minority (No) class
- A confusion matrix visualization
- Training and evaluating a Decision Tree model for comparison
- A side-by-side metrics comparison table
- A written interpretation of the results and the effect of class imbalance

## How to run

1. Install dependencies:
   ```
   pip install -r requirements.txt
   ```
2. Open the notebook:
   ```
   jupyter notebook student_employability_classification1.ipynb
   ```
3. Run all cells in order.

## Key findings

- Logistic Regression: accuracy 0.9715, precision 0.9785, recall 0.9922,
  F1-score 0.9853 on the default (Yes) class.
- On the minority (No) class specifically, Logistic Regression's precision
  drops to 0.6910 and recall to 0.4448 — it misses more than half of the
  students who are actually not likely to be hired, despite the high
  headline accuracy.
- Decision Tree: accuracy 0.9457, precision 0.9735, recall 0.9699 on the
  Yes class — slightly lower overall accuracy than Logistic Regression on
  this run.
- The gap between the strong Yes-class metrics and the much weaker No-class
  metrics is the central finding of this project: accuracy alone hides how
  poorly the model handles the minority class, which is exactly why the
  brief calls for precision/recall/F1 in addition to accuracy.

## Data leakage note

Two columns were deliberately excluded from the features because they are
strongly correlated with the target itself: `employability_status`
(categorical, near-restatement of hireability) and `job_readiness_score`
(correlates with the target at roughly 0.60, far higher than any genuine
feature, with a stark mean gap between the two classes). Including either
would make the model appear far more accurate than it actually is at
learning real, independent predictive patterns.

## Repository

https://github.com/m-waqar-tahir/vortextech-aiml-week2

## Status

✅ Completed

## Author

Muhammad Waqar Tahir
Vortex Tech AI & ML Internship 2026 — Week 2
=======

## Status

Completed — Jul 7, 2026.
>>>>>>> 89e741b038bf2076e658d633f72077f9479f38ef
