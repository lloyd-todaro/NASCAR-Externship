
# Section 4: Recommendations

## 4.1 Primary Recommendation

### Cheddar's Scratch Kitchen

**Recommendation**: Cheddar's Scratch Kitchen represents the strongest
visibility-per-dollar opportunity for NY Racing, contingent on verifying its
cost estimate before finalizing budget.

**Why this recommendation**:

1. **Best efficiency of the five tracked sponsors**: 39.9 visibility points
   per $M invested, roughly 1.5x the next-best sponsor (Progressive).
2. **Not just a "cheap" pick**: #2 in total visibility (195.6 points),
   trailing only Progressive, despite the second-smallest race count (12).
3. **Lowest financial commitment of the top-2 visibility performers**: an
   estimated $4.9M, versus Progressive's $18.0M for the #1 spot.

**Key metrics**:
- Visibility Score: 195.6 points (Rank #2 of 5)
- Efficiency: 39.9 pts/$M (Rank #1 of 5)
- Estimated Investment: $4.9M (range $2.7M-$7.1M, low-medium confidence)

**Risk factors**:
- **Cost estimate is unverified**: the $4.9M figure borrows Castrol's own
  sourced per-race rate rather than a disclosed number for this specific
  deal. If true cost runs $7-8M, efficiency falls to roughly Castrol's range
  and the "clear leader" framing no longer holds. *Mitigation*: get a direct
  quote or better-sourced comparable before committing budget.
- **Small sample, high volatility**: 12 races with the highest
  week-to-week score variance of the five sponsors (CV = 1.42). *Mitigation*:
  revisit the ranking once 10-15 more races are on record.

---

## 4.2 Alternative Recommendation

### Progressive

**Best for**: Organizations prioritizing maximum total exposure and cost
certainty over efficiency.

**Why consider this alternative**:

1. **Highest total visibility by a wide margin**: 477.6 points, driven by
   the strongest on-track performance of any tracked sponsor (4 wins, 11
   top-5s in 20 races — a 55% top-5 rate).
2. **Best-sourced cost estimate of the group**: medium confidence, versus
   Cheddar's low-medium confidence.

**Key metrics**:
- Visibility Score: 477.6 points (Rank #1 of 5)
- Efficiency: 26.5 pts/$M (Rank #2 of 5)
- Estimated Investment: $18.0M

**Trade-off**: roughly 3.7x Cheddar's estimated cost for a visibility-rank
upgrade rather than an efficiency upgrade. Right choice if budget certainty
and maximum reach matter more than return per dollar.

If Cheddar's cost verification comes back unfavorable, **Castrol** is the
well-sourced middle option (see Section 4.3, Scenario C) — smaller sample
(11 races) but a sourced, medium-confidence cost estimate and reasonable
efficiency (24.1 pts/$M).

---

## 4.3 Strategic Scenarios

### Scenario A: Maximize Visibility

| Metric | Value |
|--------|-------|
| Recommended Sponsor | Progressive |
| Visibility Score | 477.6 |
| Efficiency | 26.5 pts/$M |
| Investment Required | $18.0M |

**Best for**: Teams with budget flexibility prioritizing brand exposure

### Scenario B: Maximize Efficiency

| Metric | Value |
|--------|-------|
| Recommended Sponsor | Cheddar's Scratch Kitchen |
| Visibility Score | 195.6 |
| Efficiency | 39.9 pts/$M |
| Investment Required | $4.9M |

**Best for**: Teams prioritizing ROI justification

### Scenario C: Balanced Approach / Hedge

| Metric | Value |
|--------|-------|
| Recommended Sponsor | Castrol |
| Visibility Score | 108.3 |
| Efficiency | 24.1 pts/$M |
| Investment Required | $4.5M |

**Best for**: Teams wanting a defensible middle option with better-sourced
cost data than Cheddar's, if Cheddar's/RCR isn't the right brand fit or its
cost verification comes back unfavorable

[Insert scenario_comparison.png]

For NY Racing's current situation, we recommend **Scenario B (Cheddar's
Scratch Kitchen)** as the lead option, with **Scenario C (Castrol)** as the
fallback — see Section 4.1/4.2 for the full reasoning.

---

## 4.4 Implementation Guidance

### Recommended Next Steps

1. **Immediate**: Request a direct cost quote (or a better-sourced
   comparable) for the Cheddar's Scratch Kitchen / Kyle Busch / RCR No. 8
   deal — the single number that could flip this recommendation.
2. **Short-term (1-2 weeks)**: Run a sentiment check on the Kyle Busch
   Reddit/YouTube corpus (`sentiment_analysis.ipynb`) to confirm the
   visibility is net-positive before pitching this externally.
3. **Medium-term (1 month)**: Revisit the ranking once Cheddar's and Castrol
   (both under 12 tracked races) have accumulated more races, to confirm the
   efficiency lead holds up beyond the current small sample.

### Additional Research Recommended

Before finalizing any sponsorship decision, we recommend:

1. **Direct cost verification**: Obtain an actual cost quote or a genuinely
   comparable disclosed Cup deal for a similarly-profiled driver.
2. **Sponsor fixed-effects regression**: Test whether some sponsors carry a
   visibility premium independent of on-track performance, using data
   already in `scored_dataset.csv` / `master_dataset.csv` (no new data
   needed).
3. **Multi-season validation**: Re-run this ranking once additional seasons
   are available, to test whether the 2025-2026 pattern holds.
4. **Activation assessment**: Evaluate non-visibility benefits (hospitality,
   B2B networking) that this analysis does not capture (see Section 2.5).
5. **Brand fit analysis**: Assess alignment between sponsor brand and NY
   Racing's values, particularly for Cheddar's given Kyle Busch's polarizing
   public profile.

---

## 4.5 Decision Framework

For future sponsorship evaluation, apply this framework:

| Step | Action | Deliverable |
|------|--------|-------------|
| 1 | Collect performance data | Race results dataset |
| 2 | Gather visibility metrics | Social + media data |
| 3 | Calculate visibility score | Normalized composite |
| 4 | Research cost estimates | Cost range table |
| 5 | Compute efficiency | Visibility per dollar |
| 6 | Run sensitivity test | Stability assessment |
| 7 | Make recommendation | Decision document |

This methodology can be applied to evaluate future sponsorship opportunities
using the same analytical framework.

