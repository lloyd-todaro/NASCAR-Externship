
# Sensitivity Analysis Results

**Generated**: 2026-08-16 23:30

## Summary

The visibility scoring model was tested with four weight configurations to assess
ranking stability.

### Weight Scenarios Tested

| Scenario | Performance | Visibility | Events |
|----------|-------------|------------|--------|
| Baseline | 40% | 50% | 10% |
| Performance Heavy | 50% | 40% | 10% |
| Media Heavy | 30% | 60% | 10% |
| Equal Weights | 33.33% | 33.33% | 33.33% |

## Key Findings
Regardless of the weight configuration, the top-ranked sponsor remained consistent,
indicating that the model is robust to reasonable variations in weight assumptions.
### Rank Stability

| primary_sponsor           |   min_rank |   max_rank |   rank_range |
|:--------------------------|-----------:|-----------:|-------------:|
| Busch Light               |          5 |          5 |            0 |
| Castrol                   |          4 |          4 |            0 |
| Cheddar's Scratch Kitchen |          2 |          3 |            1 |
| Love's Travel Stops       |          6 |          6 |            0 |
| Other/Unknown             |          2 |          3 |            1 |
| Progressive               |          1 |          1 |            0 |

### Weight Impact

Insignificant

## Conclusions


**Model is ROBUST.** Rankings are stable across different weight configurations.
The top performer remains #1 under all tested scenarios. This suggests that the
relative visibility of sponsors is not sensitive to reasonable weighting choices.


## Recommendations

1. Use baseline weights (40/50/10) for primary analysis
2. Note sensitivity findings in methodology section
3. Consider presenting rankings under multiple scenarios if stakeholders have
   strong preferences about weight priorities

---
*This analysis demonstrates model robustness to stakeholder questions about
weight selection.*
