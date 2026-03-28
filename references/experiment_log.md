# Experiment Log — Digital Advertising Regression Project

## How to use this log
Update this file after every meaningful change to your notebook.
Tag each run: `baseline` · `tuned` · `promising` · `fail`

---

## Log

### Experiment 1
- **Date:** March 2026
- **Tag:** `baseline`
- **Dataset:** global_ads_performance_dataset.csv (1,800 rows · 14 columns)
- **Algorithm:** OLS Linear Regression
- **Target variable:** revenue (USD)
- **Features used:** ad_spend, clicks, impressions, conversions, CTR, CPA,
  platform, campaign_type, industry, country
- **Parameters:** Default OLS (no regularization)
- **Metrics:** R²: — · RMSE: — · MAE: —
- **Notes:** Baseline run. Fill metrics after running Cell 8.

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
