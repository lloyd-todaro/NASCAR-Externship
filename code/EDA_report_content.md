
# NASCAR Sponsorship ROI: Exploratory Data Analysis Report

## Executive Summary

This analysis examined the relationship between NASCAR race performance and
sponsorship visibility across 5 sponsors during the 2025 Cup Series season and the first half of the 2026 cup series season.

**Key Finding:** wins disproportionately effect ROI

**Correlation Strength:** Finish position shows a weak
correlation with social media visibility (r = 0.25, p < 0.01).

**Top Performers:** Progressive, Castrol, and Busch achieved the
highest visibility scores, averaging 15 points above the median.

**Primary Hypothesis for Model:** Wins give disproportionate visibility,
AND finih position correlates non-linearly with visibility

## Methodology

Data sources:
- Race results: Racing Reference
- Reddit mentions: Arctift Shift
- YouTube engagement: YouTube Data API
- News coverage: Manual tracking and Web Scraping

Analysis period: 2025 NASCAR Cup Series (36 races) and 2026 So Far (17 races)
Sponsors analyzed: [Progressive, Busch Light, Castrol, Cheddar's Scratch Kitchen, Love's Travel Stops]

## Key Findings

1. **Performance matters, but not linearly**
   top 3 finishes have a higher rate of increasing visibility, and wins even more so

2. **Channel differences**
   News data was unreliable due to tiny sample size, though high news visibility
   was typically accompanied by spikes in reddit and youtube as well. Generally Reddit was the most
   reliable data source but the correlations are in the same direction and of similar magnitude.

3. **Seasonal patterns**
   some races have automatic visibility bump across sponsors and across cars 

## Visualizations
code/data/Plots/bar_sponsor_visibility.png
code/data/Plots/correlation_heatmap.png
code/data/Plots/heatmap_weekly_exposure.png
code/data/Plots/line_visibility_trends.png
code/data/Plots/scatter_with_regression.png
code/data/Plots/stacked_channel_breakdown.png


## Hypotheses for Scoring Model

1) non-linearity of media-rank correlation
2) Playoff multiplier validation
3) Cross-sponsor normalization

## Next Steps

These findings will inform the visibility scoring model in Project 4:
1. Weight finish position at approximately 20% based on correlation strength
2. Include win bonus multiplier of 2.1x
3. Apply playoff adjustment of 28%
4. TBD
