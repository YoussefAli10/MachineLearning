# Predicting Iron Deficiency Without Anemia Using Machine Learning

CIS 631 — Machine Learning

## Project Description

This project explores whether iron deficiency without anemia can be predicted using non-laboratory information, including dietary habits, demographic characteristics, lifestyle factors, and reproductive history.

Our goal was to investigate whether these variables could help identify individuals who may be iron deficient without requiring blood measurements as model inputs.

## Dataset

We used publicly available data from the National Health and Nutrition Examination Survey (NHANES), conducted by the Centers for Disease Control and Prevention (CDC).

Our final dataset included 2,397 nonpregnant women between the ages of 20 and 44 across three NHANES periods:

- 2009–2010: 793 participants
- 2015–2016: 662 participants
- 2017–March 2020: 942 participants

Of these participants, 262 met our primary definition of iron deficiency without anemia.

We used 27 non-laboratory predictors covering demographics, nutrition, physical activity, smoking, supplement use, and reproductive history.

Ferritin measurements were used to determine iron-deficiency status, while hemoglobin and other laboratory information were used to define the study population. These laboratory measurements were excluded from the main prediction models.

## Methods

We developed our models using 1,455 participants from the 2009–2010 and 2015–2016 NHANES cycles. We then evaluated their performance on 942 participants from the 2017–March 2020 cycle.

Six machine learning models were evaluated:

1. Logistic Regression
2. Random Forest
3. Histogram Gradient Boosting
4. Decision Tree
5. K-Nearest Neighbors (KNN)
6. Support Vector Machine (SVM)

Model performance was assessed using metrics including AUROC, average precision, recall, and precision. Cross-validation was used during model development.

We also evaluated a separate model using complete blood count (CBC) measurements to compare the predictive value of laboratory and non-laboratory information.

## Results

Logistic regression performed best among the six non-laboratory models, achieving an AUROC of 0.593 and an average precision of 0.138 on the later-cycle evaluation dataset.

The CBC-based comparison model performed considerably better, achieving an AUROC of 0.816.

Overall, the non-laboratory models demonstrated limited ability to distinguish participants with iron deficiency from those without it.

These findings suggest that predicting iron deficiency without anemia using the available dietary, lifestyle, demographic, and reproductive information is challenging.

## Limitations

Our study was limited by the size of the eligible population, the availability of certain predictors, and the accuracy of self-reported dietary and lifestyle information.

Additionally, because the later NHANES cycle was included in earlier exploratory analyses, our final evaluation represents retrospective cycle-based testing rather than fully independent external validation.

Future research could examine additional predictors, more detailed information about menstrual blood loss and dietary intake, or alternative datasets.

## Notebook

The primary notebook for this project is:

`CIS631_Iron_Deficiency_6_Models_Final.ipynb`

The notebook contains the data preparation, preprocessing, model development, evaluation, and additional analyses completed throughout the project.

It was developed using Python and Google Colab. To run the notebook, open it in Colab and execute the cells sequentially. An internet connection is required to retrieve the public data sources.

## Data Sources

- [National Health and Nutrition Examination Survey (NHANES)](https://www.cdc.gov/nchs/nhanes/)
- [USDA Agricultural Research Service — Food Patterns Equivalents Database](https://www.ars.usda.gov/)
