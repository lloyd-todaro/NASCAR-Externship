
# Visibility Scoring Model - Validation Report

**Generated**: 2026-08-16 23:30

## Summary

| Check Category | Passed | Failed | Notes |
|----------------|--------|--------|-------|
| Performance Correlation | 3 | 0 | |
| Event Impact | 3 | 0 | |
| Anomaly Detection | - | 6 anomalies | |

## Detailed Results

### Performance-Visibility Correlation

- **finish_visibility_correlation**: PASS (r = -0.985)\n- **wins_visibility_correlation**: PASS (r = 0.949)\n- **laps_visibility_correlation**: PASS (r = 0.951)\n

### Event Impact Validation

- **win_impact**: PASS\n- **playoff_impact**: PASS\n- **finish_impact**: PASS\n

### Anomalies Identified

- [LOW] Progressive has high score variance (CV = 0.84)\n- [LOW] Cheddar's Scratch Kitchen has high score variance (CV = 1.42)\n- [LOW] Busch Light has high score variance (CV = 0.80)\n- [LOW] Castrol has high score variance (CV = 0.90)\n- [LOW] Love's Travel Stops has high score variance (CV = 1.32)\n- [HIGH] 3 races have zero or negative visibility scores\n

## Recommendation

**Model validation flagged issues.**

Review the failed checks and anomalies above. Consider:
1. Adjusting variable weights if correlations are weak
2. Investigating specific anomalies for data quality issues
3. Re-running with modified parameters if needed

Complete the industry comparison template before proceeding.
