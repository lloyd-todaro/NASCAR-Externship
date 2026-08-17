# NASCAR Sponsorship Visibility Analysis: Executive Summary

**Prepared for:** NY Racing
**Author:** Lloyd Todaro
**Date:** August 16, 2026
**Data:** 2025 NASCAR Cup Series (36 races) + 2026 season-to-date (17 races) · 5 tracked sponsors (Progressive, Castrol, Busch Light, Love's Travel Stops, Cheddar's Scratch Kitchen)

Visibility, performance, and cost figures below reflect only the races each
sponsor actually carried as primary on the car, based on the per-race sponsor
field scraped race-by-race from racing-reference.info — not a driver's full
season. Sample sizes vary: 11 races for Castrol and 12 for Cheddar's Scratch
Kitchen up to 29 for Love's Travel Stops, so treat the point estimates as
directional, especially for the smaller-sample sponsors.

---

## Bottom Line

On-track performance drives sponsor visibility, but not in a straight line — wins and top-5 finishes produce step-changes in exposure that a simple "better finish = more visibility" model misses. **Cheddar's Scratch Kitchen is the strongest efficiency pick**: #2 in total visibility and #1 in efficiency by roughly 3x the next-best sponsor. That result rests on a low-confidence cost estimate and a 12-race sample, and should be verified before budget is committed. **Progressive** delivers the most total exposure and the strongest on-track performance (4 wins, 11 top-5s in 20 races) at a large premium. **Castrol** is a smaller, better-sourced fallback if Cheddar's cost verification comes back unfavorable.

---

## What the Data Shows

| Finding | Evidence | So what? |
|---|---|---|
| Wins produce a step-change in visibility, not a gradual one | Wins generate **2.10x** the visibility of non-wins; top-5 finishes generate **2.03x** the visibility of finishes outside the top 10, even though the raw finish-position correlation is moderate (r = -0.34, p < 0.001) | Sponsorship value should be priced on **win/top-5 probability**, not average finish alone — a car that finishes 15th most weeks but wins twice is worth more than the average-finish number suggests |
| Playoff races carry a built-in visibility bump | +28.2% visibility in playoff races vs. regular season, independent of finish position | Time sponsor activations (new logo reveals, promos) to land inside the playoff window for free extra reach |
| Some sponsors get visibility their results don't explain | Castrol posts higher mean YouTube engagement than its finish-position trend alone would predict | This "baseline visibility" effect is real in the descriptive data but has **not been statistically tested** — see New Hypothesis A below before relying on it |
| Reddit is the most trustworthy visibility signal | Reddit has the single strongest and most significant correlation with performance (r = -0.34 with finish position, p < 0.001); YouTube is weaker; news is too sparse to use alone despite one high-magnitude reading (r = 0.26 with laps led) | Weight Reddit signal more heavily in any future live-monitoring dashboard; treat news spikes as confirmatory, not primary |

---

## Sponsor Recommendation Snapshot

| Sponsor | Races | Total Visibility | Visibility Rank | Est. Cost/yr | Efficiency (pts/$M) | Efficiency Rank |
|---|---|---|---|---|---|---|
| **Progressive** | 20 | 477.6 | #1 | $18.0M | 26.5 | #2 |
| **Cheddar's Scratch Kitchen** | 12 | 195.6 | #2 | $2.5M (low confidence) | **78.2** | **#1** |
| Busch Light | 25 | 177.0 | #3 | $13.0M | 13.6 | #5 |
| Castrol | 11 | 108.3 | #4 | $4.5M (medium confidence) | 24.1 | #3 |
| Love's Travel Stops | 29 | 71.0 | #5 | $4.5M | 15.8 | #4 |

- **Primary recommendation: Cheddar's Scratch Kitchen.** #2 total visibility and #1 efficiency by roughly 3x. **Caveat:** the $2.5M cost behind that efficiency number is a low-confidence estimate ($1.5M-$4M range) with no disclosed source for this specific deal, and the 12-race sample carries the highest score volatility of the five sponsors (CV = 1.42) — get a real quote and let more races play out before committing budget.
- **If budget allows and cost certainty matters more:** Progressive — most total exposure and the best on-track performance of any sponsor (4 wins, 11 top-5s in 20 races), at roughly 7x Cheddar's estimated cost.
- **Fallback if Cheddar's cost verification is unfavorable:** Castrol — smaller sample (11 races) but a sourced, medium-confidence cost estimate.
- **Not recommended:** Busch Light — worst efficiency of the five (13.6 pts/$M) on a real 25-race sample, zero wins or top-5s, at the third-highest cost. Love's Travel Stops — weakest visibility and second-worst efficiency despite the largest sample (29 races).

---

## Caveats to Resolve Before This Goes to a Budget Decision

**1. Verify the Cheddar's Scratch Kitchen cost estimate.**
The primary recommendation hinges on a $2.5M cost estimate with no disclosed source for this specific deal — it's inferred from team tier and comparable partial-season Cup deals. A driver of Kyle Busch's profile may command more than a typical mid-tier rate. If true cost is $6-8M, efficiency falls from 78.2 to roughly Castrol's range, and the recommendation should default to Castrol or Progressive.

**2. Two validation steps in this project disagree with each other, and the more impressive number is the less trustworthy one.**
`docs/validation_report.md` reports very high correlations (r ≈ 0.95–0.99) between visibility and performance. Those are computed on the 5-6 row sponsor-season summary table, not the race-level dataset — a handful of aggregated points will produce high correlations almost by construction. The real, race-level relationship (`code/correlation_results.csv`, N = 97) is more moderate: r = -0.34 for finish position, r = 0.23 for laps led vs. Reddit mentions. The race-level numbers are the honest ones and are already the basis for the tiered-visibility model; the validation report's headline correlations should be labeled as a sponsor-level sanity check, not model validation.

**3. Small samples for Castrol and Cheddar's Scratch Kitchen widen the uncertainty on their numbers.**
11 and 12 races respectively is enough to see a real signal (both are directionally consistent with their descriptive stats), but not enough for tight confidence — a single big or bad week moves their season totals substantially more than it would for Love's Travel Stops (29 races) or Busch Light (25 races).

**4. The "model is robust to weight choices" claim is weaker evidence than it sounds.**
`docs/sensitivity_analysis.md` shows the top-ranked sponsor is stable across four weighting schemes. With visibility scores this spread out (Progressive at 477.6 vs. Love's at 71.0), almost no reasonable reweighting would reorder them — so this demonstrates the sponsor gaps are large, not that the model's internal logic is well-calibrated.

---

## Which Existing Hypotheses Are Too Obvious to Lead With

These are fine as internal model inputs, but they won't move a stakeholder conversation because they confirm what's already assumed:

- **"Wins and top-5s generate more visibility than other finishes."** Nobody sponsoring a race car expects otherwise. Useful for calibrating the scoring model's tiering, not as a headline finding.
- **"Playoff races generate more visibility than regular-season races."** Higher playoff viewership is a given in racing. Actionable only in a narrow way — timing of activations — not sponsor selection.
- **"Reddit correlates with performance better than YouTube."** True and worth keeping as a modeling weight, but it's a data-engineering detail, not something NY Racing can act on directly.

---

## New Hypotheses Worth Testing — All Answerable From Data You Already Have

**A. Formally test the "sponsor baseline" effect.**
Run a regression of race-level visibility on finish position + laps led + win + playoff, adding sponsor fixed effects (dummy variables), using the existing `scored_dataset.csv` / `master_dataset.csv` (no new data needed). If the sponsor dummies stay significant after controlling for performance, that's real, quantified evidence that some brands earn a visibility premium independent of results — directly useful in a sponsorship negotiation.

**B. Verify the Cheddar's cost estimate — the single highest-leverage open question in the whole analysis.**
The "Cheddar's is the best pick" conclusion rests on an inferred $2.5M cost with no disclosed source. Get a direct quote, or find a genuinely comparable disclosed Cup deal for a similarly-profiled driver, and re-run the efficiency ranking. This is the one number that could flip the primary recommendation to Castrol or Progressive.

**C. Test whether Cheddar's and Castrol's efficiency holds up as more races accumulate.**
Both are working from ~11-12 race samples with high week-to-week volatility. Re-run the ranking once each has another 10-15 races on record to see if the efficiency lead is a stable pattern or a small-sample artifact.

**D. Test for a post-win "afterglow" effect using the weekly data you already have.**
Using `weekly_scores.csv`, check whether visibility stays elevated for 1-2 races after a win/top-5 before reverting, versus snapping back immediately. If afterglow exists, that tells NY Racing exactly when to schedule a sponsor activation for maximum inherited attention.

**E. Run a sentiment check on the Cheddar's/Kyle Busch data.**
Kyle Busch is a polarizing personality. The project already has `sentiment_analysis.ipynb` — run it against the Reddit/YouTube corpus to confirm Cheddar's visibility is net-positive rather than partly controversy-driven, before leaning on it in a pitch.

---

## Recommended Next Steps

1. Verify the Cheddar's Scratch Kitchen cost estimate directly (Hypothesis B) — this is the one number the primary recommendation now hinges on.
2. Run Hypothesis A (sponsor fixed-effects regression) — the most decision-relevant open modeling question, and the data is already in hand.
3. Run a sentiment pass (Hypothesis E) on the Kyle Busch corpus before pitching Cheddar's externally.
4. Revisit the ranking once Castrol and Cheddar's Scratch Kitchen have another 10-15 tracked races (Hypothesis C) to confirm the efficiency lead holds up.
