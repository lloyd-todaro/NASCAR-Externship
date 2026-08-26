# NASCAR Sponsorship Visibility Analysis

A data-driven analysis of NASCAR Cup Series sponsorship value, built for NY Racing to compare
sponsorship opportunities and identify the best value investment.

## Project Purpose

NY Racing wanted to know which NASCAR Cup Series sponsorship would deliver the most
visibility for its money. This project builds a composite **visibility score** for five
candidate sponsors — Progressive, Cheddar's Scratch Kitchen, Castrol, Busch Light, and
Love's Travel Stops — by combining on-track race performance with media and social
engagement data from the 2025 season through 2026 season-to-date, then weighs each
sponsor's visibility against its estimated cost to find the best efficiency play.

The final deliverables are in [`final_products/`](final_products/): a full written report,
an executive summary, a slide deck, and supporting methodology/validation documents.

## Methods

1. **Data collection** — race results were scraped from Racing Reference, historical
   results pulled from a Kaggle dataset, Reddit mentions collected via Arctic Shift,
   YouTube engagement pulled via the YouTube Data API, and news mentions gathered through
   manual tracking and web scraping. Sponsorship cost estimates were built from Forbes and
   Sports Business Journal coverage, team/sponsor press releases, and comparable-deal
   analysis.
2. **Cleaning & merging** — raw pulls were standardized (driver/sponsor names, dates,
   race IDs) and merged into a single master dataset keyed by sponsor and race week.
3. **Visibility scoring model** — each race week is scored as a weighted composite:
   race performance (40%, primarily laps led), a PCA-weighted media/social visibility
   index across Reddit, YouTube, and news (50%), and special-event bonuses for wins (6%)
   and playoff races (4%). All inputs are z-score normalized before weighting; see
   [`final_products/methodology.md`](final_products/methodology.md) for the full
   variable list and formula.
4. **Efficiency analysis** — season-total visibility is divided by estimated sponsorship
   cost to rank sponsors on visibility-per-dollar, not just raw exposure.
5. **Validation** — the model was stress-tested against alternative weight schemes
   (performance-heavy, media-heavy, equal-weight) and a range of cost estimates; rankings
   held stable across all tested scenarios (see
   [`final_products/sensitivity_analysis.md`](final_products/sensitivity_analysis.md) and
   [`final_products/validation_report.md`](final_products/validation_report.md)).
6. **Statistical testing** — correlations between each visibility channel and race finish
   were tested for significance; only Reddit mentions cleared standard significance
   thresholds at the collected sample size.

## Folder Structure

```
final_products/        Final deliverables: written report, executive summary, slide deck,
                        methodology, data dictionary, and supporting analysis docs
    recommendations/    Per-sponsor recommendation write-ups

plots/                 All generated charts and figures (PNG)

data_collection/       Notebooks that pull data from source: race results scraping,
                        Kaggle historical data, YouTube API, Reddit (Arctic Shift), Google API setup

csvs/                  Data files
    raw/                Source data as collected, before cleaning
    processed/          Cleaned, standardized, and merged datasets used in analysis
    external/           Third-party reference data

cleaning_and_analysis/ Notebooks for cleaning, merging, scoring, statistical testing,
                        visualization, and the final analysis/slide build, plus the EDA
                        report and supporting notes (weighting rationale, hypotheses)
```

## Data Sources

- **Race results**: Racing Reference (scraped), Kaggle NASCAR historical dataset
- **Social media**: Reddit via Arctic Shift, YouTube Data API
- **News**: Manual tracking and web scraping
- **Cost estimates**: Forbes, Sports Business Journal, press releases, comparable deals

## Environment Setup

1. Install Anaconda or Python 3.11+
2. Create environment: `conda create -n nascar-visibility python=3.11`
3. Activate: `conda activate nascar-visibility`
4. Install packages: `pip install pandas numpy matplotlib seaborn jupyter beautifulsoup4 requests praw google-api-python-client`
