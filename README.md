# 🩺 Diabetes Modeling: Progression Regression vs. Risk Classification

## 💼 Business use case

These two notebooks approach diabetes analytics from different decision points. The **progression model** estimates a continuous one-year disease-progression outcome, making it useful as an interpretable forecasting baseline. The **XGBoost model** addresses a screening-style problem by estimating whether a patient belongs to the diabetes-positive class.

The distinction matters because the models are not competing for the same job. One supports understanding and forecasting of a continuous clinical outcome; the other supports prioritization in a binary risk workflow.

## 🎯 Principal objective

The **linear-regression notebook** uses ordinary least squares on the NCSU diabetes dataset, first fitting a full specification and then a reduced model based on statistically significant predictors. Its goal is to retain useful predictive power while keeping the model transparent and easy to inspect.

The **XGBoost notebook** trains a nonlinear tree-ensemble classifier on eight patient-level predictors from a 768-row dataset. Its goal is to rank and classify diabetes risk on held-out observations, with particular attention to discrimination rather than coefficient interpretation.

## 🔎 Summary of takeaways

The regression model reaches **R² = 0.524** and an **out-of-sample R² = 0.477** on the full training specification and **R² = 0.470** and **0.485 out-of-sample R²** with the reduced model. Its main strength is interpretability and a linear baseline with great predictive power.

The XGBoost classifier reports **74.03% test accuracy** and **82.61% ROC-AUC**. Its stronger signal is the ROC-AUC, which shows useful ranking ability even though the default classification threshold leaves room for improvement. For screening, the operating threshold should be chosen around sensitivity, false-negative cost, and available follow-up capacity.

The metrics should not be compared directly: R² measures continuous prediction quality, while accuracy and ROC-AUC evaluate binary classification. Together, the notebooks show two complementary modeling styles, one prioritizing transparency and continuous outcome estimation, the other prioritizing nonlinear discrimination and risk ranking.

## 🧭 Explore the code

Review both notebooks to compare the modeling choices side by side: OLS diagnostics and feature reduction in the [progression project](https://github.com/saels/diabetes-prediction/blob/d6b36b770e27511b7b07747d42a5c3c5690be9e8/Diabetes_linear_regression_NCSU_dataset.ipynb), versus boosted trees, probability ranking, and classification evaluation in the [risk project](https://github.com/saels/diabetes-prediction/blob/d6b36b770e27511b7b07747d42a5c3c5690be9e8/Diabetes_XGBoost_classifier.ipynb). The code makes the difference between an interpretable statistical baseline and a higher-flexibility machine-learning classifier especially clear.
