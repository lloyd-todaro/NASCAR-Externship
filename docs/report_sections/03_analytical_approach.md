
## 2.3 Visibility Scoring Model

### Overview

We developed a composite visibility score that combines three top-level categories
into a single metric for sponsor comparison. The model is designed to answer:
"How much visibility exposure did this sponsor receive during the season?"

### Score Components and Weights

| Category | Weight | Components | Rationale |
|----------|--------|------------|-----------|
| **Race Performance** | 40% | Laps led (40%) | On-track dominance drives camera time and attention. Laps led is used instead of finish position because the two are highly collinear, and laps led showed the stronger relationship with visibility in EDA — including both would double-count the same signal. |
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
rest of the scale — laps led in particular is heavily skewed, with most races
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
  described above — laps led carries the race-performance signal instead.
- **Wins** are defined as a 1st-place finish.
- **Playoff races** are races 27-36, matching NASCAR's actual 10-race
  playoff window.
- All variables are drawn from `scored_dataset.csv`, the output of applying
  this model to every sponsor-race combination in the tracked window.

