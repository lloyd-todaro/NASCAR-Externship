
# Executive Summary

## Overview

This report presents a comprehensive analysis of NASCAR Cup Series sponsorship visibility
for NY Racing's strategic planning. Using data from the 2025 season and 2026
season-to-date, we developed a quantitative visibility scoring model to compare
sponsorship opportunities and identify the best value investments.

**Scope**: 5 primary sponsors analyzed across 53 tracked races (each sponsor's own race count ranges from 11 to 29, reflecting races it actually carried as primary sponsor)

**Methodology**: Composite visibility score incorporating race performance (40%),
a PCA-weighted visibility index across Reddit/YouTube/news (50%), and special
events: wins and playoffs (10%)

---

## Key Findings

### Finding 1: Efficiency leadership doesn't track brand prestige

Cheddar's Scratch Kitchen (Kyle Busch, Richard Childress Racing) delivers the best
visibility-per-dollar of any tracked sponsor (roughly 1.5x the next-best sponsor)
while carrying a budget comparable to Castrol's and far below Progressive's. It
isn't a "cheap but small" pick either: it's #2 in total visibility, trailing only
Progressive, which costs roughly 3.7x as much.

**Supporting evidence**: Efficiency 39.9 pts/$M vs. 26.5 pts/$M for Progressive, the next-best (efficiency rank #1 of 5). Total visibility 195.6 points (rank #2 of 5) on an estimated $4.9M budget.

### Finding 2: A playoff race is worth more than double a regular-season race

The visibility bump from playoff races isn't a marginal effect. A playoff race is
worth more than double a regular-season one, a bigger swing than the win bonus
(1.79x) and second only to the top-5 bonus (3.12x). Sponsors should treat
playoff-window races as prime, high-value activation windows, not just "more of the
same, but with higher stakes."

**Supporting evidence**: Average visibility in playoff-window races (race 27-36) is 129% higher than in regular-season races, across 20 playoff sponsor-entries vs. 77 regular-season entries.

### Finding 3: Reddit is the only channel with a statistically reliable signal

Of the three visibility channels tracked, only Reddit's relationship with race
performance clears standard statistical significance thresholds with a reasonably
sized sample. YouTube and news readings are directionally similar but not
statistically distinguishable from noise at this sample size. That's a real constraint on
how much weight either should carry in future live monitoring.

**Supporting evidence**: Reddit mentions vs. finish position: r = -0.34, p = 0.0006, N = 97 (the strongest and most significant relationship in the correlation matrix). YouTube views vs. finish position: r = -0.20, p = 0.055 (not significant at the 0.05 level). News mentions vs. finish position: r = -0.13, p = 0.20 (not significant).

---

## Top-Line Results

| Metric | Leader | Score |
|--------|--------|-------|
| **Highest Visibility** | Progressive | 477.6 points |
| **Best Efficiency** | Cheddar's Scratch Kitchen | 39.9 pts/$M |
| **Visibility Range** | All sponsors | 71 - 478 points |
| **Efficiency Range** | All sponsors | 13.6 - 39.9 pts/$M |

![Sponsor visibility dashboard: season totals, weekly score distribution, cumulative trend, and wins vs. visibility](../code/data/plots/sponsor_dashboard.png)

The cumulative-visibility panel (bottom left) shows Progressive separating from the field early and extending the lead again at the playoff mark (Finding 2). The other four sponsors stay bunched together for most of the season, until Cheddar's Scratch Kitchen overtakes Busch Light in the final third, the same efficiency story told numerically in Finding 1. The wins-vs-visibility panel (bottom right) makes that finding visual: Progressive is the only sponsor with any wins, yet Cheddar's Scratch Kitchen still out-visibilities Castrol and Love's Travel Stops by a wide margin.

---

## Recommendations

### Primary Recommendation

**Cheddar's Scratch Kitchen** is recommended as the primary sponsorship target based on:
- Best efficiency of the five sponsors (39.9 pts/$M, ~1.5x Progressive)
- #2 total visibility (195.6 points) despite the smallest budget in the group
- Lowest financial commitment required to secure a top-2 visibility outcome

**Estimated investment**: $4.9M (low-medium confidence estimate; verify directly before committing, see caveats) | **Expected visibility**: ~196 points

### Alternative Option

**Progressive** offers the strongest total exposure for teams prioritizing maximum reach over cost efficiency:
- #1 total visibility (477.6 points), driven by the strongest on-track performance of any sponsor (4 wins, 11 top-5s in 20 sponsored races)
- Best-sourced, medium-confidence cost estimate of the group, but at roughly 3.7x Cheddar's estimated cost

**Castrol** is a smaller, well-sourced hedge if Cheddar's cost verification comes back unfavorable, though it is no longer a standout on either visibility or efficiency once restricted to its actual 11 sponsored races.

### Recommended Next Steps

1. Verify the Cheddar's Scratch Kitchen cost estimate directly (a quote or a better-sourced comparable). It's the single number that could flip this recommendation.
2. Run a sentiment check on the Kyle Busch Reddit/YouTube corpus to confirm the visibility is net-positive before pitching this externally.
3. Revisit the ranking once Cheddar's and Castrol (both under 12 tracked races) have accumulated more races, to confirm the efficiency lead holds up beyond the current small sample.

---

## Important Caveats

This analysis relies on **estimated sponsorship costs** derived from industry publications.
Actual costs may vary significantly from estimates. Cheddar's Scratch Kitchen's estimate
in particular carries low-medium confidence with no disclosed source for this specific deal. Rankings are sensitive to:

- Cost estimate accuracy (tested with sensitivity analysis): Cheddar's efficiency lead could shrink or disappear if true cost exceeds ~$7M
- Small sample sizes for Castrol (11 races) and Cheddar's Scratch Kitchen (12 races), which widen the uncertainty on their numbers relative to Progressive (20), Busch Light (25), and Love's Travel Stops (29)
- Weight configuration choices (model is nominally robust to weight changes, though this mostly reflects large gaps between sponsors' scores rather than fine-grained model calibration)
- 2025-2026 season-specific patterns (may not generalize to future seasons)

See Section 6 (Limitations) for complete discussion.

---

*For detailed methodology, see Section 2. For complete findings, see Sections 3-4.
For recommendation rationale, see Section 5.*
