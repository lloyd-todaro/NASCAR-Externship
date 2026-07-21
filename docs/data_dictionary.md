
# Data Dictionary: NASCAR Sponsorship ROI Master Dataset

**File**: `master_dataset.csv`
**Created**: 2026-07-21
**Records**: 276 sponsor-race combinations
**Coverage**: 2024 NASCAR Cup Series (Races 1-36)
**Sponsors**: FedEx, NAPA, McDonald's, Ally, Busch Light

---

## Data Sources

| Source | Type | Collection Method | Records |
|--------|------|-------------------|---------|
| Race Results | Performance | Racing Reference | 53 |
| Reddit | Social Media | rss endpoint | 222 |
| YouTube | Video | YouTube Data API v3 | 137 |
| News | Traditional Media | web scrape | 36 |

---

## Column Definitions

### Identifier Columns

| Column | Type | Description | Example |
|--------|------|-------------|---------|
| `race_number` | integer | Sequential race number in 2024 season (1-36) | 1 |
| `race_name` | string | Official race name | "Daytona 500" |
| `race_date` | date (YYYY-MM-DD) | Date race was held | "2024-02-18" |
| `sponsor` | string | Primary sponsor name (standardized) | "FedEx" |
| `merge_key` | string | Unique identifier for joining (race_number_sponsor) | "1_FedEx" |

### Race Performance Columns

| Column | Type | Description | Range |
|--------|------|-------------|-------|
| `finish_position` | integer | Final finishing position in race | 1-40+ |
| `laps_led` | integer | Number of laps leading the race | 0-500+ |

**Notes**:
- Lower finish_position = better performance (1st place is best)
- Laps led indicates on-track visibility (car at front of field)

### Reddit Exposure Columns

| Column | Type | Description | Source |
|--------|------|-------------|--------|
| `reddit_mentions` | integer | Count of r/NASCAR posts mentioning sponsor | PRAW search |

**Notes**:
- Values of 0 indicate no mentions found (not missing data)
- Scores reflect value at collection time, not race time
- Search covered multiple term variations per sponsor

### YouTube Exposure Columns

| Column | Type | Description | Source |
|--------|------|-------------|--------|
| `youtube_total_video_count` | integer | Count of videos featuring sponsor/driver | Title keyword match |
| `youtube_total_view_count` | integer | Total views on sponsor-relevant videos | YouTube API |
| `youtube_total_like_count` | integer | Total likes on sponsor-relevant videos | YouTube API |
| `youtube_total_comment_count` | integer | Total comments on sponsor-relevant videos | YouTube API |


**Notes**:
- Total_views represents race exposure; sponsor_views represents sponsor-specific exposure
- Video tagging based on title containing sponsor/driver name
- View share = (sponsor_video_views / total_race_views) * 100

### News Exposure Columns

| Column | Type | Description | Source |
|--------|------|-------------|--------|
| `news_total_mentions` | integer | Total news articles mentioning sponsor | Manual search |
| `news_primary_mentions` | integer | Articles where sponsor was main focus | Classified |
| `news_weighted_mentions` | float | Mentions weighted by source tier | Calculated |
| `news_secondary_mentions` | integer | Articles where sponsor was secondary focus | Classified |
| `news_passing_mentions` | integer | Articles where sponsor was not focus but was mentioned | Classified |


**Notes**:
- Source tiers: Tier 1 (ESPN, NASCAR.com) = 1.0, Tier 2 = 0.8, Tier 3 = 0.6, Tier 4 = 0.4
- Primary vs secondary classification based on headline/body focus
- Search covered week following each race

---

## Missing Value Treatment

All exposure metrics use 0 for missing values, indicating:
- Reddit: No posts found mentioning sponsor in r/NASCAR
- YouTube: No videos found featuring sponsor/driver
- News: No articles found in search

This is distinct from NULL, which would indicate data was not collected.

---

## Known Limitations

1. **Reddit temporal accuracy**: Scores reflect current values, not values at race time
2. **YouTube search coverage**: Highlights only; may miss user-generated content
3. **News search depth**: Limited to first 10 results per search; may miss niche sources
4. **Sponsor tagging**: Keyword-based; may miss contextual mentions or misclassify

---

## Example Queries

### Basic: Filter to one sponsor
```python
fedex_df = master_df[master_df['sponsor'] == 'FedEx']