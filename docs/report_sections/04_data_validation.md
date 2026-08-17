
## 2.4 Data Validation and Sensitivity Testing

### 2.4.1 Model Validation Checks

Three categories of automated checks were run against the scored dataset
(`scored_dataset.csv`) before using it for ranking and recommendations.

**Performance-visibility correlation** (sponsor-season level, N=5 tracked sponsors):

| Check | Result | Expected Direction | Status |
|-------|--------|---------------------|--------|
| Average finish position vs. total visibility | r = -0.985 | Negative | PASS |
| Total wins vs. total visibility | r = 0.949 | Positive | PASS |
| Total laps led vs. total visibility | r = 0.951 | Positive | PASS |

These sponsor-season correlations are a directional sanity check on only 5
aggregated points, and a handful of aggregated points will produce very high
correlations almost by construction. The statistically meaningful read is the
race-level relationship in `correlation_results.csv` (N = 97): Reddit
mentions vs. finish position, r = -0.34, p = 0.0006. Treat the sponsor-level
numbers above as confirmation the model points the right direction, not as
model validation in the statistical sense.

**Event impact validation** (race level):

| Check | Result | Status |
|-------|--------|--------|
| Wins score meaningfully higher than non-wins | 1.79x | PASS |
| Playoff races score higher than regular-season races | +129% (2.29x) | PASS |
| Top-5 finishes score higher than finishes outside the top 20 | 3.12x | PASS |

**Anomaly detection** (6 flagged, all reviewed):

- **5 low-severity**: every tracked sponsor shows real week-to-week score
  variance (coefficient of variation ranging from 0.80 for Busch Light to
  1.42 for Cheddar's Scratch Kitchen). Expected, given that wins and
  playoff races create step-changes rather than smooth week-to-week
  visibility, and the smaller-sample sponsors (Cheddar's, Castrol) show the
  widest swings.
- **1 high-severity**: 3 race-sponsor combinations score at or near zero.
  These are races where a sponsor's car had no laps led, no win, no playoff
  bonus, and no media mentions that week — the model's theoretical floor,
  not a data quality issue.

### 2.4.2 Weight Sensitivity Testing

To test whether conclusions depend on the specific 40% race performance /
50% visibility index / 10% special events weighting, the model was rerun
under four category-weight configurations:

| Scenario | Race Performance | Visibility Index | Special Events |
|----------|-------------------|-------------------|-----------------|
| Baseline | 40% | 50% | 10% |
| Performance Heavy | 50% | 40% | 10% |
| Media Heavy | 30% | 60% | 10% |
| Equal Weights | 33.3% | 33.3% | 33.3% |

**Results**: 4 of the 5 tracked sponsors held the exact same visibility rank
in all four scenarios (Progressive #1, Castrol #4, Busch Light #5, Love's
Travel Stops last among the comparison groups). Cheddar's Scratch Kitchen
was the only tracked sponsor whose rank moved, swinging between #2 and #3
depending on how much weight a scenario gives to race performance versus
media visibility — consistent with its actual profile of strong Reddit/
YouTube engagement paired with minimal on-track dominance (39 laps led
across 12 races, the second-lowest of the five tracked sponsors).

**Caveat on reading this as "robustness"**: the visibility gaps between
sponsors are large (Progressive at 477.6 points vs. Love's Travel Stops at
71.0), so almost any reasonable reweighting preserves the same broad
ordering. Rank stability here demonstrates that the sponsor gaps are large,
not that the model's internal weight calibration is finely tuned — a
smaller, more closely-matched sponsor set would likely show more rank
movement under the same weight changes.

**A second caveat specific to this test**: the comparison set technically
includes "Other/Unknown" (every untracked car aggregated into one bucket)
alongside the five named sponsors. That bucket's combined laps-led total
(12,895, versus 23-839 for any single tracked sponsor) pushes it into the
#2-#3 rank range under performance-heavy weighting, despite representing no
individual sponsor's real visibility. Its presence in this specific ranking
is a bookkeeping artifact of including untracked cars, not a sponsor
comparison, and should be disregarded when reading the sensitivity results.

