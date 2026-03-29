# Processed Data
Train/test split files are saved in Kaggle output directory.

Files generated:
- X_train.csv — 1,440 rows, 23 features (training features)
- X_test.csv  — 360 rows, 23 features (test features)
- y_train.csv — 1,440 rows (training target: revenue)
- y_test.csv  — 360 rows (test target: revenue)
- split_metadata.json — split parameters and reproducibility info
- fitted_preprocessors.pkl — fitted StandardScaler

Split strategy: random with stratification on 5 revenue quantile bins
Random state: 42
