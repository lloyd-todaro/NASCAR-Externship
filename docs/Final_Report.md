# NASCAR Sponsorship Visibility Analysis
## Final Report for NY Racing

**Prepared by**: Lloyd Todaro
**Date**: August 18, 2026
**Version**: 1.0

---

## Table of Contents

1. Executive Summary
2. Methodology
   - 2.1 Data Sources
   - 2.2 Sponsor Selection
   - 2.3 Visibility Scoring Model
   - 2.4 Data Validation and Sensitivity Testing
   - 2.5 Assumptions and Limitations
3. Findings
   - 3.1 Efficiency Leadership Doesn't Track Brand Prestige
   - 3.2 A Playoff Race Is Worth More Than Double a Regular-Season One
   - 3.3 Reddit Is the Only Channel With a Statistically Reliable Signal
   - 3.4 On-Track Performance and Visibility Move Together, But Not Proportionally
4. Recommendations
   - 4.1 Primary Recommendation
   - 4.2 Alternative Recommendation
   - 4.3 Strategic Scenarios
   - 4.4 Implementation Guidance
   - 4.5 Decision Framework
5. Appendices
   - A. Full Data Tables
   - B. Methodology Details
   - C. Code Repository Guide

---

# Section 1: Executive Summary

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

---

# Section 2: Methodology

# Section 2: Methodology

## 2.1 Data Sources

This analysis draws on four primary data categories collected for the 2025 NASCAR Cup Series season and 2026 season-to-date.

### Race Performance Data

| Source | Data Type | Collection Method | Records |
|--------|-----------|-------------------|---------|
| Racing Reference | Race results | Web Scrape (BeautifulSoup) | 53 races |

**Fields collected**:
- Race name, date, track
- Driver, team, finish position
- Laps led, stage points
- DNF/crash flags

**Data quality notes**:
- Web scraper built with BeautifulSoup, pulling race-by-race result pages
- No missing race records for tracked sponsors
- Primary sponsor identification uses the per-race sponsor field, matched
  against each tracked driver's sponsor keywords for that specific race,
  not a driver's full-season assignment

### Social Media Data

| Source | Data Type | Collection Method | API/Tool |
|--------|-----------|-------------------|----------|
| Reddit (r/NASCAR) | Post mentions | Arctic Shift | Python script |
| YouTube | Video engagement | YouTube Data API v3 | Python script |

**Reddit data fields**:
- Number of posts
- Sponsor mention flag

**YouTube data fields**:
- Video title
- View count, like count
- Upload date
- Sponsor relevance flag

**Collection period**: July 9 - August 16, 2026 (2025 season data collected
first; 2026 season-to-date and sponsor-specific supplements collected
through mid-August)

**Rate limiting**: YouTube Data API is quota-limited (~100 units per search
call), with short delays paced between per-driver queries. Reddit (Arctic
Shift) has no fixed published rate limit; requests use retry-with-backoff to
handle intermittent failures.

### News Coverage Data

| Source | Data Type | Collection Method |
|--------|-----------|-------------------|
| GDELT DOC 2.0 API + BigQuery GKG (Global Knowledge Graph) | News article mentions | Automated query, restricted to a curated list of ~19 NASCAR/motorsports and general sports domains (ESPN, NASCAR.com, Fox Sports, Jayski, Frontstretch, Speedway Media, and others), with article text fetched and cached for sponsor keyword matching |

**Collection window**: Monthly windows spanning February-December 2025 and February-December 2026.

**Weighting approach** (4-tier source weighting):
- Tier 1 (ESPN, NASCAR.com, Fox Sports, CBS Sports, NBC Sports): Weight = 1.0
- Tier 2 (Speedway Media, motorsport.com): Weight = 0.8
- Tier 3 (Jayski, Frontstretch, si.com, and any unlisted domain by default): Weight = 0.6
- Tier 4 (reserved for lower-tier blogs/fan sites, none currently mapped): Weight = 0.4

### Cost Estimate Data

| Source | Data Type | Reliability |
|--------|-----------|-------------|
| Forbes NASCAR coverage | Sponsorship valuations | Medium |
| Jayski | Deal/partnership reports | Medium |
| Speedway Media | Partnership announcements | Low-Medium |
| RTR Sports | Cost benchmarks | Low-Medium |
| NASCAR.com / NBC Sports / ESPN press coverage | Partnership announcements | Medium |

**Note**: Exact sponsorship costs are confidential. All figures are estimates based on publicly available information.

---

## 2.2 Sponsor Selection

Five primary sponsors were selected for analysis based on:

1. **Data availability**: Sufficient race, social, and media data
2. **Team diversity**: Mix of top-tier, mid-tier, and small-team organizations
3. **Sponsor stability**: Consistent primary or near-primary presence across the tracked window
4. **Visibility**: Clear livery presence for attribution

**Selected sponsors**:
| Sponsor | Team | Driver | Team Tier |
|---------|------|--------|-----------|
| Progressive | Joe Gibbs Racing | Denny Hamlin | Top |
| Cheddar's Scratch Kitchen | Richard Childress Racing | Kyle Busch | Mid |
| Castrol | RFK Racing | Brad Keselowski | Mid-to-top |
| Love's Travel Stops | Front Row Motorsports | Todd Gilliland | Small/underfunded |
| Busch Light | Trackhouse Racing | Ross Chastain | Mid |

---

## 2.3 Visibility Scoring Model

### Overview

We developed a composite visibility score that combines three top-level categories
into a single metric for sponsor comparison. The model is designed to answer:
"How much visibility exposure did this sponsor receive during the season?"

### Score Components and Weights

| Category | Weight | Components | Rationale |
|----------|--------|------------|-----------|
| **Race Performance** | 40% | Laps led (40%) | On-track dominance drives camera time and attention. Laps led is used instead of finish position because the two are highly collinear, and laps led showed the stronger relationship with visibility in EDA. Including both would double-count the same signal. |
| **Visibility Index** | 50% | Reddit mentions, YouTube views, and weighted news mentions, combined via PCA | Captures total cross-channel exposure using data-driven relative weights between channels, rather than an analyst hand-picking a split between Reddit/YouTube/news |
| **Special Events** | 10% | Race wins (6%), Playoff races (4%) | Wins and playoff races generate disproportionate visibility spikes that a smooth performance metric alone would miss |

### Visibility Index Construction

The 50% Visibility Index is itself a composite, built as follows:

1. Each channel (Reddit mention count, YouTube total view count, news weighted
   mentions) is z-score standardized.
2. Principal Component Analysis (PCA) is fit across the three standardized
   channels; the first principal component's loadings become the data-driven
   relative weights between channels.
3. Each channel's loading is additionally scaled by
   sqrt(non-zero sample count / total sample count), so a channel with much
   sparser coverage (news: 36 of 223 sponsor-races) doesn't get overweighted
   relative to a channel with near-complete coverage (Reddit: 222 of 223).
4. The resulting composite is shifted to be non-negative
   (`Visibility_Score_Shifted`).

### Normalization Method

Continuous inputs (laps led and the visibility index) are z-score standardized
rather than min-max normalized, so a single outlier race doesn't compress the
rest of the scale. Laps led in particular is heavily skewed, with most races
recording 0 laps led and a handful recording 200+.

Binary flags (`is_win`, `is_playoff`) are kept as plain 0/1 indicators rather
than z-scored, since z-scoring a category flag would rescale it by an
arbitrary sample standard deviation rather than add meaningful information.

The weighted composite of all standardized and binary components is
calculated first in raw units; the full result is then rescaled to a single
0-100 scale in one final min-max transformation, rather than rescaling each
variable individually before combining.

### Special Cases

- **Finish position** is tracked in the scoring configuration but carries
  zero effective weight in the final model, for the collinearity reason
  described above: laps led carries the race-performance signal instead.
- **Wins** are defined as a 1st-place finish.
- **Playoff races** are races 27-36, matching NASCAR's actual 10-race
  playoff window.
- All variables are drawn from `scored_dataset.csv`, the output of applying
  this model to every sponsor-race combination in the tracked window.

---

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
  bonus, and no media mentions that week: the model's theoretical floor,
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
media visibility. That's consistent with its actual profile of strong Reddit/
YouTube engagement paired with minimal on-track dominance (39 laps led
across 12 races, the second-lowest of the five tracked sponsors).

**Caveat on reading this as "robustness"**: the visibility gaps between
sponsors are large (Progressive at 477.6 points vs. Love's Travel Stops at
71.0), so almost any reasonable reweighting preserves the same broad
ordering. Rank stability here demonstrates that the sponsor gaps are large,
not that the model's internal weight calibration is finely tuned. A
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

---

## 2.5 Assumptions and Limitations

### Key Assumptions

| Assumption | Implication | Mitigation |
|------------|-------------|------------|
| Social data represents fan engagement | Reddit/YouTube may not capture full audience | Acknowledged as proxy metrics |
| Cost estimates are accurate | Efficiency rankings depend on cost accuracy | Tested with cost ranges; see Section 2.4 sensitivity results |
| 2025-2026 patterns are representative | Results may not generalize to other seasons | Framed as a two-season analysis, not a multi-year trend |
| News search captures relevant coverage | May miss some media mentions outside the tracked domain list | Used a consistent domain list and query methodology across all sponsors |

### Known Limitations

#### 1. Cost Estimate Uncertainty

**Issue**: Exact sponsorship costs are confidential. Our estimates are derived from
industry publications and comparable-deal analysis, and may differ from actual
contract values. This is most acute for Cheddar's Scratch Kitchen, whose $4.9M
estimate borrows Castrol's own sourced per-race rate rather than a disclosed
figure for the Cheddar's/RCR deal specifically.

**Impact**: Efficiency rankings could shift if actual costs differ significantly
from estimates. Cheddar's efficiency lead over Progressive is the primary
recommendation's single largest point of uncertainty.

**Mitigation**: Tested efficiency rankings with low, mid, and high cost estimates
for every sponsor (see `sensitivity_analysis.md` and Section 2.4). Recommended
next step: a direct quote or better-sourced comparable for the Cheddar's deal.

#### 2. Small Sample Sizes for Two of the Five Sponsors

**Issue**: Castrol (11 races) and Cheddar's Scratch Kitchen (12 races) have
roughly a third of the tracked races that Love's Travel Stops (29) has, and
under half of Busch Light (25).

**Impact**: A single strong or weak week moves these two sponsors' season
totals substantially more than it would for the higher-race-count sponsors:
both show the highest score volatility of the five (CV = 0.90 and 1.42
respectively, see Section 2.4 anomaly detection).

**Mitigation**: Flagged directionally rather than treated as precise point
estimates; recommended revisiting the ranking once each has 10-15 more races
on record.

#### 3. Proxy Metrics for Visibility

**Issue**: True "visibility" is difficult to measure directly. We use proxy
metrics (mentions, views, finish position) rather than a direct visibility
measurement.

**Impact**: The model captures correlates of visibility, not visibility itself.

**Mitigation**: Selected proxies with a demonstrated statistical relationship to
performance (see Section 2.4 validation), and weighted the most reliable
channel (Reddit) most heavily in that composite.

#### 4. Two-Season Scope

**Issue**: Analysis covers the 2025 season and 2026 season-to-date. Results may
not apply to other seasons with different competitive dynamics, driver
lineups, or sponsorship structures.

**Impact**: Cannot predict future sponsor performance from this data alone.

**Mitigation**: Framed conclusions as specific to the 2025-2026 window.
Recommended validation with additional seasons before locking in a multi-year
sponsorship decision.

#### 5. Social Media Timing

**Issue**: Social media metrics were collected at a point in time (July 9 -
August 16, 2026) and may have changed since collection.

**Impact**: Engagement numbers represent a snapshot, not real-time values.

**Mitigation**: Collected data within a consistent window across all sponsors,
so relative comparisons remain fair even if absolute counts have since moved.

#### 6. Activation Not Measured

**Issue**: Sponsorship value includes activation (hospitality, B2B networking,
in-market promotions) that cannot be measured with public data.

**Impact**: Analysis captures visibility only, not total sponsorship ROI.

**Mitigation**: Clearly scoped this analysis as "visibility," not full ROI.

---

### What This Analysis Can and Cannot Tell You

| This Analysis CAN Tell You | This Analysis CANNOT Tell You |
|---------------------------|------------------------------|
| Relative visibility rankings of the five analyzed sponsors | Whether sponsorship is a good investment overall |
| Which sponsors deliver the most visibility per estimated dollar | Actual sponsorship costs |
| How race performance correlates with visibility, and how strongly (Section 2.4) | Whether past visibility predicts future visibility |
| Which events (wins, playoffs, top-5s) generate the most visibility | How visibility translates to sponsor business outcomes |

---

*For questions about methodology, contact Lloyd Todaro (lloydltodaro@gmail.com).*

---

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

---

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
   top-5s in 20 races, a 55% top-5 rate).
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
well-sourced middle option (see Section 4.3, Scenario C), a smaller sample
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

![Scenario comparison: visibility and efficiency by strategic scenario](../code/data/plots/scenario_comparison.png)

For NY Racing's current situation, we recommend **Scenario B (Cheddar's
Scratch Kitchen)** as the lead option, with **Scenario C (Castrol)** as the
fallback. See Section 4.1/4.2 for the full reasoning.

---

## 4.4 Implementation Guidance

### Recommended Next Steps

1. **Immediate**: Request a direct cost quote (or a better-sourced
   comparable) for the Cheddar's Scratch Kitchen / Kyle Busch / RCR No. 8
   deal. It's the single number that could flip this recommendation.
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

Future sponsorship decisions can reuse this same framework.

---

## Appendix A: Full Data Tables

### Final Rankings (Visibility and Efficiency)

| primary_sponsor           |   total_visibility |   visibility_rank |   cost_mid |   efficiency |   efficiency_rank |   rank_stability |
|:--------------------------|-------------------:|------------------:|-----------:|-------------:|------------------:|-----------------:|
| Progressive               |              477.6 |                 1 |       18   |         26.5 |                 2 |                0 |
| Cheddar's Scratch Kitchen |              195.6 |                 2 |        4.9 |         39.9 |                 1 |                1 |
| Busch Light               |              177   |                 3 |       13   |         13.6 |                 5 |                0 |
| Castrol                   |              108.3 |                 4 |        4.5 |         24.1 |                 3 |                0 |
| Love's Travel Stops       |               71   |                 5 |        4.5 |         15.8 |                 4 |                0 |

### Efficiency Rankings (Sorted, With Cost-per-Point and Confidence)

| primary_sponsor           |   total_visibility |   visibility_rank |   cost_mid |   efficiency |   cost_per_point |   efficiency_rank | confidence   |
|:--------------------------|-------------------:|------------------:|-----------:|-------------:|-----------------:|------------------:|:-------------|
| Cheddar's Scratch Kitchen |              195.6 |                 2 |        4.9 |         39.9 |          25056   |                 1 | low-medium   |
| Progressive               |              477.6 |                 1 |       18   |         26.5 |          37686.9 |                 2 | medium       |
| Castrol                   |              108.3 |                 4 |        4.5 |         24.1 |          41533.8 |                 3 | medium       |
| Love's Travel Stops       |               71   |                 5 |        4.5 |         15.8 |          63362.9 |                 4 | medium       |
| Busch Light               |              177   |                 3 |       13   |         13.6 |          73451.8 |                 5 | low-medium   |

### Weight Sensitivity and Rank Stability

| Sponsor | Min Rank | Max Rank | Rank Range |
|---|---|---|---|
| Progressive | 1 | 1 | 0 |
| Cheddar's Scratch Kitchen | 2 | 3 | 1 |
| Castrol | 4 | 4 | 0 |
| Busch Light | 5 | 5 | 0 |
| Love's Travel Stops | 6 | 6 | 0 |
| Other/Unknown | 2 | 3 | 1 |

Rank range = how much a sponsor's visibility rank moved across the four
weight scenarios tested in Section 2.4.2 (baseline, performance-heavy,
media-heavy, equal-weights). Only Cheddar's Scratch Kitchen (and the
untracked "Other/Unknown" bucket) moved at all.

---

## Appendix B: Methodology Details

### Scoring Configuration

```json
{
  "version": "1.0",
  "created_date": "2026-07-10",
  "category_weights": {
    "race_performance": 0.4,
    "visibility_score": 0.5,
    "special_events": 0.1
  },
  "variables": {
    "finish_position": {
      "category": "race_performance",
      "weight_within_category": 0,
      "effective_weight": 0,
      "direction": "inverse",
      "transform": "invert_position"
    },
    "laps_led": {
      "category": "race_performance",
      "weight_within_category": 1,
      "effective_weight": 0.4,
      "direction": "direct",
      "transform": "normalize"
    },
    "news_weighted_mentions": {
      "category": "visibility_score",
      "weight_within_category": "N/A",
      "effective_weight": "N/A",
      "direction": "direct",
      "transform": "normalize"
    },
    "reddit_mentions": {
      "category": "visibility_score",
      "weight_within_category": "N/A",
      "effective_weight": "N/A",
      "direction": "direct",
      "transform": "normalize"
    },
    "youtube_sponsor_views": {
      "category": "visibility_score",
      "weight_within_category": "N/A",
      "effective_weight": "N/A",
      "direction": "direct",
      "transform": "normalize"
    },
    "is_win": {
      "category": "special_events",
      "weight_within_category": 0.6,
      "effective_weight": 0.06,
      "direction": "direct",
      "transform": "binary"
    },
    "is_playoff": {
      "category": "special_events",
      "weight_within_category": 0.4,
      "effective_weight": 0.04,
      "direction": "direct",
      "transform": "binary"
    }
  }
}
```

### Weighting Rationale and Design Decisions

### Why not equal weights?

Equal weights (14.3% each across the seven scored variables) would treat
Reddit mentions as equally important as race wins, and would ignore the
hierarchical importance of performance versus social engagement.

### Why not data-driven weights from regression?

Regression-based weights would require a labeled "visibility outcome"
variable, which doesn't exist; would be sensitive to sample size and
outliers, especially given the small samples for Castrol and Cheddar's
Scratch Kitchen; and would be harder to explain to stakeholders than a
transparent, fixed weighting scheme. The hybrid approach used here (fixed
category weights, with PCA determining the data-driven split *within* the
visibility index, see Section 2.3) balances transparency against letting
the data speak within the media-channel category.

---

## Appendix C: Code Repository Guide

All analysis code is available in the project repository, in pipeline order:

| File | Purpose |
|------|---------|
| `Scraping_For_Race_Results.ipynb` | Scrapes race-by-race results and per-race primary sponsor data from Racing Reference |
| `Clean_Race_Data.ipynb` | Cleans scraped race data and assigns each race's actual primary sponsor |
| `Collect_Youtube_API_Data.ipynb` | Collects YouTube video engagement data via YouTube Data API v3 |
| `reddit_arctic_shift_sentiment.ipynb` | Collects Reddit mention data via the Arctic Shift API |
| `News_Data_Collection_old.ipynb` | Collects news article mentions via the GDELT DOC 2.0 API and BigQuery GKG |
| `pytrends_data_collection.ipynb` | Collects Google Trends interest data |
| `data_merge_master.ipynb` | Merges race, social, and news data into the master dataset |
| `data_visualization.ipynb` | Builds the PCA-weighted Visibility Index and exploratory visualizations |
| `statistical_analysis.ipynb` | Runs correlation and significance testing (`correlation_results.csv`) |
| `sentiment_analysis.ipynb` | Sentiment analysis on the Reddit/YouTube text corpus |
| `ROI_Estimation.ipynb` | Computes visibility scores, cost estimates, efficiency rankings, and sensitivity testing |
| `Final_analysis.ipynb` | Compiles the report sections and this final report |

---

*End of Report*
