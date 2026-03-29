# Data Cleaning Report

## Dataset
Global Ads Performance Dataset — 1,800 rows, 14 columns
Period: January 2024 — December 2024

## Structural cleaning performed (before split)

### Duplicate check
- Exact duplicates found: 0
- Action: None required

### Missing values
- Missing values found: 0 across all 14 columns
- Action: None required

### Data type conversion
- date column converted from object to datetime64
- month extracted from date (integer 1-12)
- quarter extracted from date (integer 1-4)
- Final shape after cleaning: 1,800 rows, 16 columns

### Outlier inspection
- ad_spend: 33 outliers beyond 3 std devs
- clicks: 26 outliers
- impressions: 0 outliers
- conversions: 33 outliers
- revenue: 37 outliers
- ROAS: 47 outliers
- Decision: all retained — row-level check confirmed legitimate
  high-budget campaigns with internally consistent values

## What was NOT changed
- No rows removed
- No values imputed
- No columns renamed
- Raw data integrity preserved

## Leakage prevention
- ROAS dropped (derived from revenue)
- CPA dropped (derived from conversions and ad_spend)
- date dropped (replaced by month and quarter)

## Note on outlier detection timing
Outlier inspection was performed on the full dataset prior to splitting 
for exploratory purposes only. No rows were removed or transformed based 
on these statistics. In a production pipeline this check would be 
performed on training data only.
