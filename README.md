# Predicting Iron Deficiency Without Anemia Using Machine Learning

CIS 631 — Machine Learning

## Project Description

This project investigates whether iron deficiency without anemia can be predicted using non-laboratory information, including dietary intake, demographic characteristics, lifestyle factors, and reproductive history.

The goal was to evaluate whether these variables could help identify individuals who may be iron deficient without using blood measurements as model predictors.

## Dataset

We used publicly available data from the National Health and Nutrition Examination Survey (NHANES), conducted by the Centers for Disease Control and Prevention (CDC).

Our final analytic dataset contained **3,066 nonpregnant women ages 20–44** across four NHANES periods:

| NHANES Period | Participants | Purpose |
|---|---:|---|
| 2007–2008 | 669 | Independent evaluation |
| 2009–2010 | 793 | Model development |
| 2015–2016 | 662 | Model development |
| 2017–March 2020 | 942 | Model development |
| **Total** | **3,066** | |

Of these participants, 337 met our primary definition of iron deficiency without anemia.

The final models used 25 non-laboratory predictors covering dietary intake, demographics, lifestyle, and reproductive history.

Iron deficiency was defined using serum ferritin below 15 µg/L. Hemoglobin was used to exclude anemia, and C-reactive protein (CRP) was used to account for inflammation. Laboratory measurements were excluded from the main non-laboratory prediction models.

## Methodology

We used 2,397 participants from the 2009–2010, 2015–2016, and 2017–March 2020 cycles for model development.

The 2007–2008 cycle, containing 669 participants, was reserved for independent evaluation. Model selection and preprocessing decisions were made without using this cycle's outcomes.

Six machine learning models were evaluated:

1. Logistic Regression
2. Random Forest
3. Histogram Gradient Boosting
4. Decision Tree
5. K-Nearest Neighbors (KNN)
6. Support Vector Machine (SVM)

Five-fold stratified cross-validation was used during development. Model performance was evaluated using AUROC, average precision, recall, and precision.

We also developed a separate complete blood count (CBC) benchmark to compare the predictive value of blood-based and non-laboratory information.

Because laboratory methods differed across certain NHANES periods, the analysis incorporated the CDC's published ferritin harmonization equation for the 2007–2008 cycle.

## Results

The six non-laboratory models demonstrated limited predictive performance on the independent 2007–2008 evaluation dataset.

| Model | AUROC | Average Precision |
|---|---:|---:|
| Logistic Regression | 0.540 | 0.138 |
| Random Forest | 0.576 | 0.141 |
| Histogram Gradient Boosting | 0.547 | 0.135 |
| Decision Tree | 0.556 | 0.127 |
| KNN | 0.513 | 0.121 |
| SVM | 0.565 | 0.162 |
| CBC Benchmark | 0.749 | 0.348 |

Logistic regression was selected as the primary non-laboratory model based on development-set performance. Random forest achieved the highest AUROC among the non-laboratory models on the independent test set, while SVM achieved the highest average precision.

The CBC benchmark substantially outperformed the primary non-laboratory model, with an AUROC difference of 0.209 (95% bootstrap confidence interval: 0.095–0.310).

## Additional Analyses

We compared progressively larger groups of non-laboratory predictors to investigate which categories contributed useful information.

| Predictor Group | Independent-Test AUROC |
|---|---:|
| Dietary factors only | 0.535 |
| Dietary + lifestyle factors | 0.525 |
| Dietary + lifestyle + reproductive factors | 0.573 |

Adding reproductive-history variables improved discrimination relative to the smaller feature groups, although overall performance remained limited.

Additional analyses included permutation importance, coefficient interpretation, predictor-importance stability, sensitivity analysis using a ferritin threshold of 30 µg/L, and performance comparisons across individual NHANES cycles.

## Discussion and Limitations

Our findings suggest that iron deficiency without anemia is difficult to predict reliably using the non-laboratory information available in these NHANES datasets.

Several limitations should be considered:

- Self-reported dietary information may not accurately represent long-term eating habits.
- The available variables may not fully capture important factors such as menstrual blood loss or individual differences in iron absorption.
- The eligible population was restricted to nonpregnant women ages 20–44.
- The independent evaluation used an earlier NHANES cycle rather than a prospective sample.
- The machine learning performance estimates
