
# Hypotheses for Visibility Scoring Model

## Priority 1: Core Model Components

### H1: Performance-Visibility Relationship
**Hypothesis:** Each position improvement (e.g., P10 to P5) increases visibility by approximately 40%.
**Evidence:** Scatter plot shows clear negative trend; correlation = 0.24
**Model implication:** Finish position should be weighted at ~40% of total score

### H2: Win Bonus Effect
**Hypothesis:** Race wins generate 2.1x more visibility than non-wins
**Evidence:** Win multiplier calculated as 2.1x
**Model implication:** Add discrete bonus for wins (not just position weight)

## Priority 2: Modifiers and Adjustments

### H3: Playoff Multiplier
**Hypothesis:** Playoff races generate 28% more visibility than regular season
**Evidence:** Comparison shows 1 vs 0.8
**Model implication:** Apply 1.28 multiplier to playoff race scores

### H4: Channel Weighting
**Hypothesis:** Reddit mentions are more predictable from performance than YouTube
**Evidence:** R-squared values: Reddit's is greater
**Model implication:** Weight Reddit higher

## Priority 3: Sponsor-Specific Factors

### H5: Team Tier Effect
**Hypothesis:** Top-tier team sponsors receive more baseline visibility regardless of results
**Evidence:** Bottom-performing races for top teams still show high visibility
**Model implication:** Consider baseline offset for team tier

## Hypotheses to Test in Project 4

1. [ ] H1: Performance-visibility relationship (linear regression)
2. [ ] H2: Win bonus quantification
3. [ ] H3: Playoff multiplier validation
4. [ ] H4: Channel weight optimization
5. [ ] H5: Team tier baseline (if data supports)
