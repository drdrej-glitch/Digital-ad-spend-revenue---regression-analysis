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

  Feature-to-target connection analysis complete. Training set only.
  Key observations:
  - HIGH relevance: conversions, clicks, ad_spend, platform
  - MEDIUM relevance: impressions, CTR, industry, country
  - LOW relevance: CPC, quarter, campaign_type
  - Skewed features: clicks (1.11), ad_spend (1.63), conversions (1.83)
  - Zero missing values confirmed across all features
  - conversions and clicks flagged MONITOR for VIF check
  - All features compatible with OLS regression
  - No features engineered or removed at this stage
 
  Feature distribution visualization is complete on the training set only.
  4 plots saved. Key findings:
  - conversions most skewed (1.83), ad_spend (1.63), clicks (1.11)
  - Country dummies show ~14% each — expected for 7-category variable
  - All features confirmed usable for OLS as-is
  - Google Ads has 37% more training campaigns than TikTok
  - No zero variance or extreme imbalance found

  Missing value verification complete. All three checks passed —
  0 NaN values, 0 empty strings, 0 exact duplicates confirmed
  on the training set. No imputation required.

  Feature summary table complete. All 13 features documented
  with type, missing values, skewness, and OLS decision.
  Saved as feature_summary_table.csv.

  All pre-modeling steps complete:
  - Data cleaning ✓
  - Train/test split ✓  
  - Statistical preprocessing ✓
  - EDA on training set ✓
  - Feature type identification ✓
  - Feature distributions visualized ✓
  - Missing value check ✓
  - Feature summary table ✓
  Ready to build OLS baseline regression model.

  Target variable deep dive complete. Revenue confirmed right-skewed
  (skewness 2.556, kurtosis 9.391). Mean $30,180 vs median $18,763
  — $11,417 gap confirms skew. Log transformation reduces skewness
  to -0.517 — near normal. Decision confirmed: use log-transformed
  revenue for OLS. Zero negative values — log transform safe to apply.

  Numerical feature profiling is complete on the training set.
  Top 5 features profiled. Skewed features: conversions (1.83),
  ad_spend (1.63), clicks (1.11). Normal features: impressions (0.01),
  CTR (0.61), CPC (0.63). Zero variance: none. Scale mismatches:
  resolved by StandardScaler. Log transforms flagged for Experiment 2.
  Baseline OLS will use features as-is.

  Numerical feature correlation analysis complete (training set only).
  Results by strength category:

  VERY STRONG (|r| > 0.7):
  - conversions +0.828 — priority predictor

  STRONG (0.5 < |r| < 0.7):
  - clicks +0.672 — priority predictor

  MODERATE (0.3 < |r| < 0.5):
  - ad_spend +0.487 — core research variable
  - impressions +0.480 — reach signal
  - CTR +0.416 — efficiency signal

  VERY WEAK (|r| < 0.1):
  - quarter +0.033 — kept as seasonal control
  - CPC -0.012 — kept for completeness

  Strategic decision: all features retained for baseline OLS.
  CPC and quarter kept as controls despite weak correlation.
  Bar chart saved: feature_target_correlations.png

  Categorical feature analysis complete on training set.
  All 4 features have adequate sample sizes — no rare categories.

  Revenue gaps confirmed:
  - platform: $26,129 — most informative (TikTok $45,082 vs Meta $18,953)
  - country: $10,054 — Australia leads, USA last
  - industry: $6,368 — SaaS leads, Fintech last  
  - campaign_type: $3,171 — least informative, Search leads

  Key observations:
  - TikTok highest revenue with fewest campaigns (25% of data)
  - Mean >> median within every category confirms skew persists
  across all groups — reinforces log transform decision
  - All encoding decisions validated — one-hot correct for all 4

  4 plots saved to reports/figures/.

  Missing data map complete. Heatmap shows a completely solid pattern —
  zero missing values confirmed visually across all 23 features and
  1,440 training rows. No imputation required. Severity: none.
  Plot saved: missing_data_map.png


  IQR outlier detection complete on training set.
  IQR catches more than 3std method as expected for skewed data.
  conversions flagged HIGH at 5.2% — addressed:
  strongest predictor (corr 0.83), removing would lose most
  informative campaigns, log transform mitigates impact.
  All other features below 5% threshold.
  Final decision: retain all outliers across all features.
  Plot saved: iqr_outlier_boxplots.png

  VIF analysis revealed joint multicollinearity across numerical features:
  clicks (39.06), CTR (11.78), ad_spend (11.49), 
  impressions (10.93), CPC (10.50) all exceed VIF > 10 threshold.
  Root cause: clicks are correlated with multiple features simultaneously.
  conversions VIF = 6.46 — only feature below threshold.
  Decision: 
  - Experiment 1: run OLS with all features — note VIF as a limitation
  - Experiment 2: run OLS with low VIF features only — compare results
  This approach demonstrates an understanding of multicollinearity
  and its consequences for regression interpretation.

  EDA Summary Dashboard is complete. Key findings synthesized:
  - Dataset clean (0 missing, 0 duplicates)
  - Strong predictors: conversions (0.83), clicks (0.67)
  - Platform most informative categorical ($26,129 gap)
  - Main risk: joint multicollinearity (VIF > 10 for 5 features)
  - Two-experiment plan confirmed
  - Expected R²: 0.70-0.85
  - Status: READY for OLS regression
 
  Feature summary table updated with full EDA findings.
  15 features documented across 12 columns, including
  missing strategy, transform, VIF, correlation, priority
  and OLS decision for both experiments.
  HIGH priority: clicks, ad_spend, conversions, platform
  DROPPED: month (multicollinearity), ROAS/CPA (leakage), date
  Saved: feature_summary_table_updated.csv
  Ready for OLS Experiment 1.

  Binning demonstration complete on training set (educational only).
  Key finding — dataset does not require binning because:
  1. Equal-width binning destroys data — 71% of ad_spend 
   campaigns fall in a single "Very Low" bin, losing all variation
  2. Strongest predictor (conversions corr 0.83) loses power 
   when binned — 473 unique values reduced to 4 tiers
  3. StandardScaler already resolved scale differences between features
  4. Log transformation on revenue already handles non-linearity
  5. OLS works directly with continuous values — binning loses information

  Conversion-tier revenue confirmed a strong pattern:
  Top performer $108,322 vs Low performer $4,401 — but this
  information already captured by the continuous conversions column.

  Decision: binning NOT applied to OLS model.
  Useful for: stakeholder reports and Experiment 2 feature engineering.
  Plot saved: binning_strategies.png

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
