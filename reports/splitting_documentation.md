# Splitting Documentation

## Strategy chosen
Random split with stratification on revenue quantile bins

## Rationale
- 1,800 independent campaign-level observations
- No temporal dependencies between campaigns
- Revenue is right-skewed — stratification ensures balanced representation
- Rules out temporal and grouped splitting strategies

## Parameters
- Test size: 20% (360 rows)
- Training size: 80% (1,440 rows)
- Random state: 42
- Stratification: 5 equal-frequency quantile bins on revenue

## Validation results
- Training bin distribution: [288, 288, 288, 288, 288]
- Test bin distribution: [72, 72, 72, 72, 72]
- Training revenue mean: $30,179
- Test revenue mean: $29,789
- Conclusion: perfect stratification confirmed

## Reproducibility
- random_state=42 ensures identical split on every run
- All parameters saved in split_metadata.json
