
# NASCAR Sponsorship Visibility Scoring Model - Methodology

**Version**: 1.0
**Date**: 2026-08-14
**Analyst**: Lloyd Todaro

---

## Executive Summary

This document describes the methodology used to calculate visibility scores for
NASCAR Cup Series sponsors during the 2025 season and 2026 season-to-date. The model combines race
performance, media coverage, and social engagement into a composite visibility
score that enables sponsor comparison and efficiency analysis.

---

## 1. Variables and Weights

### 1.1 Selected Variables

The visibility score incorporates seven variables across four categories:

| Category | Variable | Description | Weight |
|----------|----------|-------------|--------|
| Race Performance | Laps Led | Number of laps leading | 40% |
| media coverage and social media buzz | Visibility Score | Normalized score from media mentions and social media| 50% |
| Special Events | Is Win | Binary flag for race wins | 6% |
| Special Events | Is Playoff | Binary flag for playoff races | 4% |
| **TOTAL** | | | **100%** |

### 1.2 Weight Rationale

- **Race Performance (40%)**: On-track success is the foundation of sponsor visibility.
  Better finishes mean more camera time and media attention.
- **Media Coverage and Social (50%)**: Media mentions, social media engagement, and
  YouTube video coverage are strong indicators of public awareness and sponsor
  visibility.
- **Special Events (10%)**: Wins and playoff races generate disproportionate
  visibility spikes.

---

## 2. Data Sources

### 2.1 Race Performance

| Source | Data Type | Collection Method |
|--------|-----------|-------------------|
| Racing Reference | Race results | Web Scrape |


### 2.2 Media and Social

| Source | Data Type | Collection Method |
|--------|-----------|-------------------|
| Reddit (r/NASCAR) | Post mentions | Arctic Shift |
| YouTube | Video engagement | YouTube Data API |
| News sites | Article mentions | Manual search + tracking + Web Scraping |

### 2.3 Cost Estimates

Sponsorship cost estimates derived from:
- Forbes NASCAR coverage
- Sports Business Journal articles
- Team/sponsor press releases
- Comparable deal analysis

---

## 3. Scoring Methodology

### 3.1 Normalization

All variables are normalized to a 0-100 scale using z-score normalization


**Special cases:**
- **Finish position**: Inverted (lower position = higher score)
- **YouTube views**: Log-transformed before normalization (reduces outlier impact)
- **Binary flags**: Scaled to 0 or 100

### 3.2 Score Calculation

Weekly visibility score:
score = (0.4 * laps_led_z) + (0.5 * visibility_z) + (0.06 * is_win) + (0.04 * is_playoff)


Season total visibility:
total = sum of weekly scores across all races


### 3.3 Efficiency Calculation

efficiency = total_visibility / estimated_cost_mid (visibility points per $M spent)


---

## 4. Assumptions and Limitations

### 4.1 Assumptions

1. **Cost estimates are approximations** - Exact sponsorship values are confidential
2. **Social data reflects current state** - Reddit/YouTube metrics at collection time
3. **News coverage is English-only** - International coverage not tracked
4. **Equal value per exposure type** - All Reddit mentions weighted equally

### 4.2 Known Limitations

| Limitation | Impact | Mitigation |
|------------|--------|------------|
| Cost uncertainty | Efficiency rankings may shift with actual costs | Tested with cost ranges |
| Temporal accuracy | Social scores change over time | Collected within consistent window |
| Activation not measured | Hospitality, B2B value excluded | Noted as out of scope |
| Single season | Results may not generalize | Frame as 2024 analysis |

---

## 5. Sensitivity Analysis

### 5.1 Weight Sensitivity

The model was tested with alternative weight configurations:

| Scenario | Result |
|----------|--------|
| Performance Heavy (50/25/15/10) | Stable |
| Media Heavy (30/40/20/10) | Stable |
| Equal Weights (25/25/25/25) | Stable |

**Conclusion**: The top-ranked sponsor remained consistent across all tested weight scenarios, indicating that the model is robust to reasonable variations in weight assumptions.

### 5.2 Cost Sensitivity

Efficiency rankings tested with low, mid, and high cost estimates showed
stable rankings.

---

## 6. Results Summary

### 6.1 Visibility Rankings

| Rank | Sponsor | Total Visibility | Key Driver |
|------|---------|------------------|------------|
| 1 | Progressive | 767.72 | New Sponsor on an elite driver |
| 2 | Castrol | 319.92 | Solid tier driver on a longstanding sponsor |
| 3 | Busch Light | 303.03 | All around NASCAR sponsor |
| 4 | Love's Travel Stops | 99.34 | not primary |
| 5 | Chaddar's Scratch Kitchen | 65.35 | not primary |

### 6.2 Efficiency Rankings

| Rank | Sponsor | Visibility/$M | Value Proposition |
|------|---------|---------------|-------------------|
| 1 | Castrol | 71.09 | Long standing and seemingly underpriced for its performance |
| 2 | Cheddar's Scratch Kitchen | 43.5 | Cheap and effective part time sponsorship |
| 3 | Progressive | 42.65 | High visibility but expensive |
| 4 | Busch Light | 23.3 | Expensive but iconic sponsor |
| 5 | Love's Travel Stops | 22.08 | Not primary, low visibility |
---

## 7. Appendix

### 7.1 Files Generated

| File | Description |
|------|-------------|
| `rankings.csv` | Final visibility and efficiency rankings |
| `scored_dataset.csv` | Full dataset with visibility scores |
| `cost_estimates.csv` | Sponsorship cost research |
| `sensitivity_analysis.md` | Weight sensitivity results |
| `validation_report.md` | Model validation results |

### 7.2 Code Repository

All analysis code is documented in:
- `code/visibility_scoring_model.ipynb`

---

*This methodology document supports the NASCAR Sponsorship ROI analysis for NY Racing.*
