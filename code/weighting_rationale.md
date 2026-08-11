
# Visibility Score: Weighting Rationale

## Overall Philosophy

The weighting scheme prioritizes **on-track performance and media exposure** because:

1. On-track results determine visibility opportunity (better finishes = more camera time)
2. Traditional media still reaches the largest audience for NASCAR content
3. Social engagement, while valuable, represents a subset of total audience

## Category Rationale

### Race Performance (40%)

*Why 40%?* Race performance is the foundation of sponsorship value. A sponsor on a winning car gets exponentially more exposure than one on a mid-pack car. Our EDA showed that finish position correlates strongly with all visibility metrics.

**Variable breakdown:**
- **Laps Led (100%)**: Laps led is a strong proxy for race dominance
### Visibility Score (50%)
*Why 50%?* Visibility score is a composite metric that captures the total exposure across all media channels. It is the most direct measure of how much attention a driver and their sponsors receive.
**Variable breakdown:**
- **Visibility Score (100%)**: This is the aggregated score from all visibility sources,
### Special Events (10%)

*Why 10%?* Wins and playoff races generate disproportionate visibility spikes that should be captured.

**Variable breakdown:**
- **Wins (60%)**: A win generates 3-5x normal visibility. Even a small bonus weight has large impact when activated.
- **Playoffs (40%)**: Playoff races have higher stakes and more viewers. Built-in visibility multiplier.

## Design Decisions

### Why not equal weights?

Equal weights (14.3% each for 7 variables) would:
- Treat Reddit mentions as equally important as race wins
- Ignore the hierarchical importance of performance vs. social

### Why not data-driven weights from regression?

Regression-based weights would:
- Require a labeled "visibility outcome" variable (which doesn't exist)
- Be sensitive to sample size and outliers
- Be harder to explain to stakeholders

The hybrid approach provides transparency and defensibility.

## Sensitivity Testing

We will test alternative weight configurations in Substep 4.3.3:
- Higher performance weight (50/25/15/10)
- Higher media weight (30/40/20/10)
- Equal weights (25/25/25/25)

If rankings change significantly under alternative weights, we'll note the sensitivity in our methodology.
