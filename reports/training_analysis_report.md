# Training Set Analysis Report

## EDA performed on training set only
1,440 rows — test set (360 rows) locked throughout

## Key findings

### Revenue distribution
- Heavily right-skewed in raw form
- Log-transformed revenue approximates normal distribution
- Decision: consider log transformation before OLS

### Correlations with revenue
- conversions: +0.83 (strongest predictor)
- clicks: +0.67
- ad_spend: +0.49
- impressions: +0.48
- CTR: +0.42
- CPC: -0.01 (negligible)
- month: +0.03 (negligible)
- quarter: +0.03 (negligible)

### Multicollinearity warnings
- clicks and conversions: 0.82 correlation — risk in OLS
- month and quarter: 0.97 correlation — drop month before OLS

### Platform analysis
- TikTok Ads: $45,082 avg revenue
- Google Ads: $30,792 avg revenue
- Meta Ads: $18,953 avg revenue
- Gap: TikTok generates 2.4x Meta revenue

### Seasonal patterns
- Q4 strongest: $32,566
- Q2 weakest: $28,479
- Monthly pattern noisy — May dip to $24,000, October peak $36,500

### Scatter plot observations
- Fan shapes in conversions, clicks, ad_spend vs revenue
- Suggests heteroskedasticity — formal test needed in diagnostics

### Country analysis
- Australia leads: $36,854
- USA last: $26,800

### Industry analysis
- SaaS leads: $33,164
- Fintech last: $26,796

## Pre-modeling decisions
1. Drop month — near-perfect correlation with quarter (0.97)
2. Consider log-transforming revenue — addresses skew
3. Test for heteroskedasticity in diagnostics cell
4. Monitor clicks/conversions multicollinearity in VIF check
