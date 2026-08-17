
# Sponsor Recommendation: Cheddar's Scratch Kitchen

**Recommendation Type**: Primary Recommendation
**Analysis Date**: 2026-08-16

---

## Executive Summary

Cheddar's Scratch Kitchen is recommended as the **primary recommendation** for NY
Racing's sponsorship strategy based on our visibility scoring analysis of the 2025
season and 2026 season-to-date, restricted to the 12 races where Cheddar's was
actually the primary sponsor on Kyle Busch's RCR No. 8.

---

## Key Metrics

| Metric | Value | Context |
|--------|-------|---------|
| **Visibility Rank** | #2 of 5 | Second only to Progressive |
| **Efficiency Rank** | #1 of 5 | ~3x the next-best sponsor (Progressive) |
| **Total Visibility** | 195.6 points | Across 12 races |
| **Efficiency** | 78.2 pts/$M | Low-confidence cost estimate — see caveat below |
| **Estimated Cost** | $2.5M/year | Low confidence; no disclosed source for this specific deal |

---

## Why This Sponsor?

### Strength 1: Best efficiency by a wide margin

Cheddar's delivers 78.2 visibility points per $M invested — roughly 3x Progressive
(26.5 pts/$M), the next-most-efficient sponsor. The visibility side of this number
(195.6 points across 12 races) is directly observed data, not an estimate.

### Strength 2: High visibility relative to sample size

Cheddar's is #2 in total visibility across all five sponsors despite the
second-smallest race count (12) — beaten only by Progressive, which ran 20 races
and costs roughly 7x as much.

### Strength 3: Kyle Busch is a genuinely high-attention driver

Kyle Busch (RCR No. 8) is a two-time Cup Series champion and one of the
most talked-about personalities in the sport, consistent with the strong Reddit and
YouTube coverage in this dataset.

---

## Supporting Data

### Performance Summary

| Category | Cheddar's Scratch Kitchen | Dataset Average (5 sponsors) |
|----------|----------------|-----------------|
| Total Visibility | 195.6 | 205.9 |
| Efficiency (pts/$M) | 78.2 | 31.6 |
| Wins | 0 | 0.8 |
| Top 5 Finishes | 1 | 3.2 |
| Top 10 Finishes | 4 | 5.8 |
| Tracked Races | 12 | 19.4 |

### Consistency Analysis

- **Best Week Score**: 83.2
- **Worst Week Score**: 1.4
- **Score Variability**: 23.1 (standard deviation) — the highest of the five sponsors (CV = 1.42), meaning visibility is spikier/less predictable week to week than Progressive's or Castrol's.

Volatile relative to the other sponsors, and on a smaller sample — the floor (worst week 1.4) and ceiling (best week 83.2) bracket a wide range, so a few more races would meaningfully sharpen this estimate.

---

## Risk Assessment

### Risk 1: Cost estimate is unverified

**What could go wrong**: The $2.5M mid estimate is inferred from team tier and a comparable-deal method, not a disclosed source — no press release or industry report gives the actual per-race Cheddar's/Kyle Busch rate.
**Likelihood**: Medium — Kyle Busch's star power could plausibly command an above-average rate for a "mid-tier team" ride.
**Impact if it occurs**: If true cost is $6-8M instead of $2.5M, efficiency falls from 78.2 to roughly 25-33 pts/$M — still competitive, but no longer a clear efficiency leader.
**Mitigation**: Get a direct quote or a better-sourced comparable before finalizing budget; don't present the 78.2 pts/$M figure to stakeholders as a settled number.

### Risk 2: Small sample and driver/brand fit

**What could go wrong**: 12 races is a small sample with high week-to-week variance, and Kyle Busch is a polarizing personality — some of his attention is negative/controversy-driven rather than pure brand affinity.
**Likelihood**: Low-Medium — doesn't undermine the visibility numbers themselves, but is a qualitative brand-safety consideration.
**Impact if it occurs**: Some fraction of impressions may carry mixed sentiment rather than pure positive brand lift, and the ranking could shift as more races accumulate.
**Mitigation**: A quick sentiment pass on the Reddit/YouTube corpus (the project already has a `sentiment_analysis.ipynb` notebook) before committing, and revisit the ranking once more races are on record.

### Cost Estimate Uncertainty

Our cost estimate of $2.5M carries **low** confidence.

- **Upside scenario**: If actual cost is at or below the $1.5M low end, efficiency improves further and this becomes an even stronger pick.
- **Downside scenario**: If actual cost is at or above the $4M high end (or beyond it), efficiency drops toward Progressive's range and the "clear leader" framing no longer holds.
- **Recommendation**: Treat this as the leading candidate pending cost verification, not a finalized pick — get a real number before committing budget.

---

## Connection to NY Racing's Situation

- **Team positioning**: A high-visibility, high-efficiency pick lets NY Racing make a strong exposure case without committing Progressive-level budget.
- **Budget considerations**: At an estimated $2.5M, this is the cheapest of the three shortlisted sponsors by a wide margin — but budget planning should use the full $1.5M-$4M range until the cost is verified, not the point estimate.
- **Strategic alignment**: Casual-dining brand with broad appeal; RCR is an established, respected Cup organization. Worth a direct fit conversation given Kyle Busch's polarizing public profile (see Risk 2).

---

## Additional Research Recommended

To strengthen this recommendation, consider:

1. **Direct cost verification**: A quote or better-sourced comparable for the actual Cheddar's/RCR No. 8 sponsorship rate — this is the single biggest open uncertainty in the whole recommendation.
2. **Sentiment check**: Run the existing sentiment analysis notebook against the Kyle Busch Reddit/YouTube corpus to confirm the visibility is net-positive for the brand.
3. **More races**: Revisit this ranking once Cheddar's has another 10-15 tracked races to confirm the efficiency lead holds up beyond the current small sample.

---

## Conclusion

Cheddar's Scratch Kitchen represents **the strongest visibility-per-dollar opportunity in the dataset, contingent on verifying its cost** — it beats every other tracked sponsor on efficiency and trails only Progressive on raw visibility, at an estimated fraction of Progressive's cost.

**Recommended action**: Pursue direct cost verification for the Kyle Busch/Cheddar's deal before finalizing a budget commitment; treat Castrol as the well-sourced fallback if verification comes back unfavorable.

---

*This recommendation is based on 2025 season and 2026 season-to-date data, restricted to races Cheddar's Scratch Kitchen actually sponsored. See methodology document for assumptions and limitations.*
