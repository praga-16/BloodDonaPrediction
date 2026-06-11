# PRCP-1011-BloodDonaPred

Blood donation prediction project for identifying whether a donor is likely to donate again in March 2007 using donor history features from the provided Taiwan blood donation dataset.

## Project objective

This project has two main goals:

- Perform complete exploratory data analysis on the donor dataset.
- Build and compare multiple machine learning models to predict repeat blood donation.

The dataset includes these main fields:

- `Months since Last Donation`
- `Number of Donations`
- `Total Volume Donated c.c.`
- `Months since First Donation`
- `Made Donation in March 2007` (target)

## Files

- `PRCP_1011_BloodDonaPred.ipynb` — main notebook containing EDA, preprocessing, model building, evaluation, and conclusion.
- `Warm_Up_Predict_Blood_Donations_-_Traning_Data.csv` — input dataset in CSV format.
- `Warm_Up_Predict_Blood_Donations_-_Traning_Data.xlsx` — input dataset in Excel format.
- `blood_donation_model_comparison.csv` — optional exported model performance summary.

## Problem statement

Blood transfusion services need to maintain enough supply for future demand. This project predicts whether a donor will donate blood the next time the mobile blood donation vehicle visits campus.

## Workflow used

### 1. Data loading

The dataset is loaded from the provided Excel or CSV file using pandas.

### 2. Data cleaning

- Removed the `Unnamed: 0` column because it acts like an index and has no predictive value.
- Checked for missing values.
- Checked duplicate rows.
- Renamed columns for easier coding and readability.

### 3. Exploratory data analysis

The notebook includes:

- Dataset shape, info, and descriptive statistics.
- Missing value analysis.
- Duplicate row analysis.
- Univariate analysis using histograms.
- Target class distribution.
- Bivariate analysis using boxplots.
- Correlation heatmap.
- Outlier visualization.

### 4. Feature and target definition

- Features: donor history variables.
- Target: `Made_Donation_March_2007`

### 5. Preprocessing

A preprocessing pipeline is used with:

- `SimpleImputer(strategy='median')`
- `StandardScaler()`

### 6. Models compared

The following models are trained and evaluated:

- Logistic Regression
- Random Forest Classifier
- Gradient Boosting Classifier
- Extra Trees Classifier
- Support Vector Machine (SVM)
- K-Nearest Neighbors (KNN)

### 7. Evaluation metrics

Models are compared using:

- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC

Stratified K-Fold cross-validation is used for more reliable model comparison.

## Best model recommendation

Logistic Regression is recommended as the production model for this project because:

- It gives strong performance on small structured tabular data.
- It is easy to interpret.
- It is fast to train and predict.
- It is less likely to overfit than more complex models on this dataset.

## Challenges faced

### Class imbalance

The target variable has more non-donors than donors. To reduce bias, stratified cross-validation and balanced models are used where applicable.

### Multicollinearity

`Number of Donations` and `Total Volume Donated c.c.` are strongly related, because total blood volume depends on the number of donations.

### Small dataset size

Since the dataset is not very large, some complex models may overfit. Cross-validation helps provide a more stable estimate of performance.

### Feature scaling

The input variables are measured on different scales, so scaling is applied before training distance-based and margin-based models.

## Libraries used

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn

## How to run

1. Open the notebook `PRCP_1011_BloodDonaPred.ipynb` in Jupyter Notebook or JupyterLab.
2. Keep the dataset file in the same working directory as the notebook.
3. Run all cells from top to bottom.
4. Review the EDA plots, model comparison table, confusion matrix, ROC curve, and final observations.

## Output

The notebook produces:

- EDA visualizations
- Model comparison report
- Best model selection
- Classification report
- Confusion matrix
- ROC curve
- Optional CSV export of model metrics

## Conclusion

This project builds an end-to-end machine learning pipeline for blood donation prediction. It combines exploratory data analysis, preprocessing, multiple model comparison, and production recommendation in a single notebook submission.
