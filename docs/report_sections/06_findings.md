
# Section 3: Findings

## 3.1 Finding: Efficiency Leadership Doesn't Track Brand Prestige

Cheddar's Scratch Kitchen (Kyle Busch, Richard Childress Racing) delivers the
best visibility-per-dollar of any tracked sponsor, despite being a mid-tier
team on a partial-season deal rather than a marquee, full-season primary.

| Sponsor | Total Visibility | Visibility Rank | Efficiency (pts/$M) | Efficiency Rank | Est. Cost |
|---------|-------------------|-------------------|------------------------|--------------------|-----------|
| Progressive | 477.6 | #1 | 26.5 | #2 | $18.0M |
| Cheddar's Scratch Kitchen | 195.6 | #2 | **39.9** | **#1** | $4.9M |
| Busch Light | 177.0 | #3 | 13.6 | #5 | $13.0M |
| Castrol | 108.3 | #4 | 24.1 | #3 | $4.5M |
| Love's Travel Stops | 71.0 | #5 | 15.8 | #4 | $4.5M |

Cheddar's is not a "cheap but small" pick. It's #2 in total visibility,
trailing only Progressive, which costs roughly 3.7x as much. Its efficiency
lead over the next-best sponsor (Progressive) is roughly 1.5x.

![Visibility efficiency and cost per point by sponsor](../code/data/plots/efficiency_comparison.png)

The cost-per-point panel on the right makes the ranking concrete: Cheddar's
Scratch Kitchen costs about $25,000 per visibility point, roughly a third of
what Busch Light costs for the same unit of exposure ($73,452) and well
below Progressive's $37,687.

**Caveat**: the $4.9M cost estimate behind this finding borrows Castrol's own
sourced per-race rate rather than a disclosed figure for the Cheddar's/RCR
deal specifically (see Section 2.4 and 2.5). This is the single largest
open question behind the ranking.

## 3.2 Finding: A Playoff Race Is Worth More Than Double a Regular-Season One

The visibility bump from playoff races is not a marginal effect:

| Event Type | Visibility Multiplier | Sample |
|------------|-------------------------|--------|
| Win vs. non-win | 1.79x | All tracked races |
| Top-5 vs. outside-top-10 finish | 3.12x | All tracked races |
| Playoff vs. regular-season race | 2.29x (+129%) | 20 playoff sponsor-entries vs. 77 regular-season entries |

The playoff effect is a bigger swing than the win bonus and second only to
the top-5 bonus, independent of finish position. Sponsors should treat
playoff-window races (races 27-36) as prime, high-value activation windows,
not just "more of the same, but with higher stakes."

By contrast, "wins and top-5s generate more visibility than other finishes"
is not, by itself, a useful headline finding: no one sponsoring a race car
expects otherwise. Its value here is calibrating the scoring model's
special-events weighting (Section 2.3), not as a stakeholder-facing insight.

## 3.3 Finding: Reddit Is the Only Channel With a Statistically Reliable Signal

Of the three visibility channels tracked, only Reddit's relationship with
race performance clears standard statistical significance thresholds at
this sample size:

| Channel | Correlation with Finish Position | p-value | N | Significant? |
|---------|-------------------------------------|---------|---|----------------|
| Reddit mentions | r = -0.34 | 0.0006 | 97 | Yes (p < 0.001) |
| YouTube views | r = -0.20 | 0.055 | 97 | No (borderline) |
| News mentions | r = -0.13 | 0.20 | 97 | No |

![Race performance vs. Reddit mentions, with Spearman correlation and trend line](../code/data/plots/scatter_with_regression.png)

Most races cluster at single-digit mention counts regardless of finish
position, the dense band along the bottom of the plot, and a small number of
high-mention races pull the trend line into negative territory. That pattern,
real but noisy rather than tight, is why Reddit clears significance at
p = 0.0006 while YouTube (p = 0.055) and news (p = 0.20) don't: 97 races is
enough to detect the underlying trend, but not enough to make it obvious
point by point.

YouTube and news readings are directionally consistent with Reddit but not
statistically distinguishable from noise at this sample size. This is a real
constraint on how much weight either should carry in a future live
monitoring dashboard. Reddit should be weighted most heavily, with YouTube
and news treated as confirmatory rather than primary signals.

## 3.4 Finding: On-Track Performance and Visibility Move Together, But Not Proportionally

| Sponsor | Avg. Finish | Wins | Top-5s | Top-10s | Total Visibility |
|---------|--------------|------|--------|---------|---------------------|
| Progressive | 10.6 | 4 | 11 | 13 | 477.6 |
| Cheddar's Scratch Kitchen | 17.5 | 0 | 1 | 4 | 195.6 |
| Castrol | 18.9 | 0 | 3 | 3 | 108.3 |
| Busch Light | 18.7 | 0 | - | - | 177.0 |
| Love's Travel Stops | 21.7 | 0 | - | - | 71.0 |

Progressive is the only tracked sponsor with any wins in the window, and its
average finish (10.6) is more than 7 spots better than the next-closest
sponsor, consistent with its #1 visibility rank. But the relationship
flattens out below that: Cheddar's, Castrol, and Busch Light post similar
average finishes (17.5-18.9) yet materially different visibility totals
(195.6, 108.3, 177.0), meaning on-track performance alone does not fully
explain the visibility gap between them. This is the gap the PCA-weighted
Visibility Index (Section 2.3) is designed to capture, and it's also why
efficiency (Section 3.1), not raw visibility, is the more decision-relevant
metric once cost is factored in.

