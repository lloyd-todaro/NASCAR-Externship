
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
from estimates — Cheddar's efficiency lead over Progressive is the primary
recommendation's single largest point of uncertainty.

**Mitigation**: Tested efficiency rankings with low, mid, and high cost estimates
for every sponsor (see `sensitivity_analysis.md` and Section 2.4). Recommended
next step: a direct quote or better-sourced comparable for the Cheddar's deal.

#### 2. Small Sample Sizes for Two of the Five Sponsors

**Issue**: Castrol (11 races) and Cheddar's Scratch Kitchen (12 races) have
roughly a third of the tracked races that Love's Travel Stops (29) has, and
under half of Busch Light (25).

**Impact**: A single strong or weak week moves these two sponsors' season
totals substantially more than it would for the higher-race-count sponsors —
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
