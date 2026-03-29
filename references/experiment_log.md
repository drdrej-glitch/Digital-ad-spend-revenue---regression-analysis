# Experiment Log — Digital Advertising Regression Project

## How to use this log
Update this file after every meaningful change to your notebook.
Tag each run: `baseline` · `tuned` · `promising` · `fail`

---

## Log

### Experiment 1
- **Date:** March 2026
- **Tag:** `baseline`
- **Dataset:** global_ads_performance_dataset.csv (1,800 rows · 16 columns after feature extraction)
- **Algorithm:** OLS Linear Regression
- **Target variable:** revenue (USD)
- **Features used:** ad_spend, clicks, impressions, conversions, CTR, CPA,
  platform, campaign_type, industry, country
- **Parameters:** Default OLS (no regularization)
- **Metrics:** R²: — · RMSE: — · MAE: —
- **Notes:** * Notes: Baseline run. Fill metrics after running OLS Regression cell.

  Data cleaning complete — 0 missing values, 0 duplicates confirmed.
  Date parsed to datetime, month and quarter extracted (now 16 columns).
  Outlier check run on 6 key columns — 47 in ROAS, 37 in revenue,
  33 in ad_spend and conversions, 26 in clicks, 0 in impressions.
  Decision: retain all outliers as they represent legitimate high-budget
  campaigns, not data errors.
  Row-level check on top 5 revenue campaigns confirmed outliers are
  legitimate — all show consistent high spend, clicks, and conversions.
  TikTok Ads appears in 4 of top 5 highest revenue campaigns.

  Data inspection complete. Key findings: TikTok Ads generates 2.4x
  more revenue than Meta Ads despite 37% fewer campaigns. Q4 shows
  strongest revenue ($33,134 avg). Search campaigns outperform all
  other types. Australia leads by country unexpectedly. SaaS is
  top industry. All findings to be confirmed by OLS regression.

  Train/test split complete. Strategy: random split with stratification
  on 5 revenue quantile bins. 1,440 training rows / 360 test rows (80/20).
  ROAS, CPA, and date dropped to prevent leakage. Categorical columns
  dummy encoded — shape expanded from 13 to 24 columns. Perfect
  stratification confirmed — all 5 bins equally represented
  (288 train / 72 test per bin). Train/test CSV files and metadata
  JSON saved to Kaggle output.

  Statistical preprocessing complete. StandardScaler fitted on 
  X_train (1,440 rows) only — applied to X_test using training 
  parameters. Training mean ~0.0 and std ~1.0 confirmed. Test set 
  slight deviation (mean: 0.009, std: 1.009) is expected and confirms 
  no leakage. All 23 features were retained for OLS. Fitted scaler saved 
  to fitted_preprocessors.pkl.
  
  EDA complete on training set only (1,440 rows — test set locked).
  Key training set findings to be confirmed by OLS:
  Revenue distribution, correlations, group differences by platform/
  industry/country/campaign type, and seasonal Q4 pattern examined.
  5 plots saved as PNG files.

  Feature-to-target connection analysis complete. Observations only —
  no features engineered or removed. Key notes: conversions and clicks
  flagged as MONITOR for VIF multicollinearity check. All features
  confirmed compatible with OLS. Zero missing values. ad_spend and
  conversions may be skewed — to check in diagnostics. Ready for OLS.

---

### Experiment 2
- **Date:**
- **Tag:**
- **Dataset:**
- **Algorithm:**
- **Target variable:**
- **Features used:**
- **Parameters:**
- **Metrics:** R²: · RMSE: · MAE:
- **Notes:**

---

### Experiment 3
- **Date:**
- **Tag:**
- **Dataset:**
- **Algorithm:**
- **Target variable:**
- **Features used:**
- **Parameters:**
- **Metrics:** R²: · RMSE: · MAE:
- **Notes:**

---

## Summary Table

| # | Date | Algorithm | Key Features | R² | RMSE | Tag |
|---|---|---|---|---|---|---|
| 1 | Mar 2026 | OLS | All features | — | — | baseline |
| 2 | | | | | | |
| 3 | | | | | | |
```

---

### Step 3 — How to update it as you work

Every time you run a new experiment in Kaggle:

1. Go to your GitHub repo → open `references/experiment_log.md`
2. Click the **pencil icon** to edit
3. Fill in the metrics from your Kaggle output
4. Scroll down → write a commit message like `"Log experiment 1 baseline OLS results"`
5. Click **Commit changes**

---

### What your workflow looks like in practice
```
Run cell in Kaggle → get R² and RMSE output
        ↓
Open experiment_log.md on GitHub
        ↓
Fill in metrics + notes
        ↓
Commit with a descriptive message
