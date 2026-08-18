
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

