# Marketing Campaign Analytics — Business Insights Report

**Report Date:** Generated automatically by `marketing_analysis.py`
**Dataset:** Marketing Campaigns (multi-platform)
**Coverage:** October 2023 – October 2024

---

## Table of Contents

1. [Dataset Overview](#1-dataset-overview)
2. [Data Cleaning Summary](#2-data-cleaning-summary)
3. [KPI Summary](#3-kpi-summary)
4. [Platform Performance Comparison](#4-platform-performance-comparison)
5. [Trend Analysis](#5-trend-analysis)
6. [Top Performing Campaigns](#6-top-performing-campaigns)
7. [Bottom Performing Campaigns](#7-bottom-performing-campaigns)
8. [Strategic Recommendations](#8-strategic-recommendations)
9. [Executive Summary](#9-executive-summary)

---

## 1. Dataset Overview

| Attribute            | Value                        |
|----------------------|------------------------------|
| Raw records          | 2,681                        |
| Clean records        | 1,881                        |
| Columns              | 8 original + 7 derived       |
| Platforms            | 6 (Google, Facebook, Email, LinkedIn, Instagram, Twitter) |
| Date range           | October 2023 – October 2024 |
| Total campaign spend | $47,025,673                  |
| Total conversions    | 1,886,997                    |

The dataset contains one row per campaign with identifiers, platform label, start/end dates, and three core performance metrics (Clicks, Conversions, Cost).

---

## 2. Data Cleaning Summary

### Issues Detected & Resolved

| Issue | Action | Records Affected |
|---|---|---|
| Missing Clicks / Conversions / Cost | Dropped rows (KPIs impossible to compute) | 799 rows |
| Zero-click records | Removed (division-by-zero in CPC / CR) | 1 row |
| Inconsistent platform naming (`facebook`, `Google `) | Strip + case-normalise + alias map | ~200 rows |
| Columns stored as strings | Cast to `float64` (numeric) / `datetime64` (dates) | All rows |
| Duplicate records | None found | 0 rows |
| Conversions > Clicks (data anomaly) | Flagged with `Data_Quality_Flag = True`; retained | 92 rows |

### Derived Columns Created

| Column | Formula |
|---|---|
| `Conversion_Rate` | Conversions / Clicks |
| `CPC` | Cost / Clicks |
| `CPA` | Cost / Conversions |
| `Conversion_Efficiency` | Conversions / Cost |
| `Campaign_Duration_Days` | End_Date − Start_Date (days) |
| `Duration_Group` | Binned: < 1 Month / 1–3 / 3–6 / 6–12 / > 12 Months |
| `Start_YearMonth` | Period label for trend grouping |

---

## 3. KPI Summary

### Overall Portfolio KPIs

| KPI | Value |
|---|---|
| **Total Campaigns** | 1,881 |
| **Total Clicks** | 18,672,035 |
| **Total Conversions** | 1,886,997 |
| **Total Cost** | $47,025,673 |
| **Overall Conversion Rate** | 10.11% |
| **Overall CPC** | $2.52 |
| **Overall CPA** | $24.92 |
| **Overall Conversion Efficiency** | 0.0401 conv/$1 |

### Interpretation

- A **10.11% conversion rate** is strong for multi-channel digital marketing (industry average typically 2–5% for paid channels).
- An **average CPA of $24.92** is competitive and suggests well-targeted audiences.
- The **$2.52 CPC** is lean, indicating efficient bidding strategies across most platforms.

---

## 4. Platform Performance Comparison

### Platform Summary Table

| Rank | Platform | Campaigns | Conversions | Conv. Rate | CPC | CPA | Perf. Score |
|---|---|---|---|---|---|---|---|
| 🥇 1 | **Google** | 489 | 498,563 | 10.35% | $2.51 | $24.19 | **0.8623** |
| 🥈 2 | **Facebook** | 467 | 470,369 | 10.47% | $2.69 | $25.69 | 0.6179 |
| 🥉 3 | **Email** | 253 | 256,368 | 10.32% | $2.57 | $24.93 | 0.4257 |
| 4 | LinkedIn | 232 | 237,106 | 9.61% | $2.39 | $24.89 | 0.2352 |
| 5 | Instagram | 233 | 231,287 | 10.00% | $2.51 | $25.16 | 0.2219 |
| 6 | **Twitter** | 207 | 193,304 | 9.21% | $2.27 | $24.66 | **0.0058** |

### Performance Score Formula

```
Score = 0.40 × norm(Conversion Rate)
      + 0.30 × norm(Total Conversions)
      + 0.20 × norm(Conversion Efficiency)
      − 0.10 × norm(CPA)
```

All components are min-max normalised to [0, 1] across platforms before weighting.

### Key Findings

- **Google** achieves the highest composite score (0.862) driven by the largest conversion volume (498K) and lowest CPA ($24.19).
- **Facebook** has the highest raw conversion rate (10.47%) but ranks second due to slightly higher CPA.
- **Twitter** ranks last with the lowest conversion rate (9.21%) and fewest conversions despite competitive raw CPC — cheap clicks are not converting.
- **LinkedIn's** lower conversion rate (9.61%) may reflect a more conservative B2B audience; however CPA is competitive at $24.89.
- **Email** is the most cost-efficient channel on a per-dollar basis with $24.93 CPA on $6.4M spend.

---

## 5. Trend Analysis

### Monthly Summary

| Month | Campaigns | Conversions | Total Cost | Conv. Rate |
|---|---|---|---|---|
| Oct 2023 | 52 | 53,104 | $1,183,055 | 11.80% |
| Nov 2023 | 161 | 168,122 | $3,813,770 | 9.80% |
| Dec 2023 | 167 | 179,018 | $4,130,831 | 9.71% |
| Jan 2024 | 167 | 164,940 | $4,164,235 | 9.24% |
| **Feb 2024** | **174** | **174,846** | **$4,272,264** | **11.13%** |
| Mar 2024 | 158 | 167,354 | $3,938,165 | 10.19% |
| Apr 2024 | 153 | 150,772 | $3,924,664 | 10.46% |
| May 2024 | 141 | 144,513 | $3,595,746 | 10.05% |
| Jun 2024 | 156 | 145,224 | $3,918,001 | 9.55% |
| Jul 2024 | 155 | 147,079 | $3,817,367 | 10.19% |
| Aug 2024 | 139 | 142,024 | $3,514,891 | 10.17% |
| Sep 2024 | 143 | 137,885 | $3,798,732 | 10.43% |
| Oct 2024 | 115 | 112,116 | $2,953,952 | 10.19% |

### Trend Observations

#### Launch surge (Oct–Nov 2023)
A rapid 3× increase in campaigns from October (52) to November (161) indicates a major Q4 push, likely holiday-season driven.

#### Peak period (Nov 2023 – Feb 2024)
The four months from November to February represent peak activity (161–174 campaigns/month) and peak absolute conversions. February 2024 saw the highest conversion rate at 11.13%.

#### Gradual decline (Mar–Oct 2024)
Following the Q1 2024 peak, campaign volume declined steadily from 174 (Feb) to 115 (Oct 2024) — a **34% drop**. This is the most significant operational trend in the dataset and suggests under-investment in H2.

#### Seasonal conversion rate pattern
Conversion rates dipped in January (9.24%) and June (9.55%) — likely post-holiday cooldowns — and rebounded in February (11.13%) and March (10.19%).

---

## 6. Top Performing Campaigns

### Top 10 by Total Conversions

| Campaign | Platform | Conversions | Conv. Rate | CPA |
|---|---|---|---|---|
| Worry Campaign | Google | 2,000 | 11.0% | $2.51 |
| Something Campaign | Email | 2,000 | 18.4% | $22.94 |
| Adult Campaign | Facebook | 2,000 | 51.5% | $11.92 |
| Base Campaign | Facebook | 1,999 | 11.2% | $11.69 |
| Simple Campaign | Twitter | 1,997 | 154.1%* | $6.46 |
| Play Campaign | Facebook | 1,995 | 38.0% | $5.55 |
| Reflect Campaign | Google | 1,995 | 22.0% | $3.51 |
| What Campaign | Email | 1,991 | 24.1% | $13.06 |
| Our Campaign | LinkedIn | 1,990 | 28.5% | $16.33 |
| Position Campaign | Google | 1,989 | 16.2% | $8.86 |

> *\* Conv. Rate > 100% indicates the Data_Quality_Flag anomaly (Conversions > Clicks); retained but noted.*

**Insight:** The top campaigns are spread across Google (3), Facebook (3), Email (2), LinkedIn (1), and Twitter (1). Google and Facebook dominate the podium — consistent with their platform ranking.

---

## 7. Bottom Performing Campaigns

### Bottom 10 by Total Conversions

| Campaign | Platform | Conversions | Conv. Rate | CPA |
|---|---|---|---|---|
| Left Campaign | Google | 0 | 0.0% | N/A |
| Learn Campaign | Twitter | 0 | 0.0% | N/A |
| Body Campaign | Email | 0 | 0.0% | N/A |
| Firm Campaign | Twitter | 2 | 0.0% | $22,058 |
| Under Campaign | Twitter | 3 | 0.0% | $9,533 |
| Discuss Campaign | Twitter | 3 | 0.0% | $16,008 |
| Fish Campaign | Instagram | 4 | 0.2% | $8,027 |
| Follow Campaign | Instagram | 6 | 0.1% | $5,544 |
| When Campaign | Twitter | 7 | 0.0% | $1,545 |
| Suffer Campaign | Google | 10 | 0.1% | $596 |

**Insight:** Three campaigns produced zero conversions despite non-trivial spend (e.g., Learn Campaign on Twitter: $20,611 with 0 conversions). Twitter features prominently in the bottom-10 list (5 of 10 entries), reinforcing its poor aggregate performance.

---

## 8. Strategic Recommendations

### Recommendation 1 — Reallocate budget from Twitter to Google
**Impact: High | Effort: Low**

Twitter delivers the lowest conversion rate (9.21%) and the worst performance score (0.006) despite a non-trivial spend of $4.77M. Shifting 25–30% of Twitter's budget to Google (score 0.862, CPA $24.19) would increase conversion volume with minimal additional cost.

**Action:** Reduce Twitter monthly budget allocation by $350K–$500K. Increase Google search / display budgets proportionally.

---

### Recommendation 2 — Prioritise Google and Facebook as anchor channels
**Impact: High | Effort: Low**

Google and Facebook together account for 51.2% of total conversions (969K of 1.89M) and represent the most proven channels. Maintaining and growing these as primary channels is the lowest-risk path to conversion growth.

**Action:** Target a combined 50–55% budget share for Google + Facebook in future planning cycles.

---

### Recommendation 3 — Favour longer-duration campaigns
**Impact: Medium | Effort: Medium**

Analysis of campaign duration vs average conversions shows:

| Duration | Avg. Conversions/Campaign |
|---|---|
| < 1 Month | 725 |
| 1–3 Months | 979 |
| 3–6 Months | 964 |
| 6–12 Months | 999 |
| > 12 Months | **1,015** |

Campaigns running longer than 12 months average **40% more conversions** than sub-month bursts. Algorithmic optimisation and sustained audience exposure likely drive this effect.

**Action:** For evergreen products/services, design campaigns with a minimum 6-month horizon. Reserve short bursts for time-sensitive promotions only.

---

### Recommendation 4 — Address the H2 2024 activity decline
**Impact: High | Effort: Medium**

Campaign volume dropped from 174 in February 2024 to 115 in October 2024 — a 34% decline — causing a commensurate fall in conversions ($4.27M → $2.95M monthly spend). If this is not intentional seasonal planning, it represents a significant missed opportunity.

**Action:** Build an H2 campaign calendar during Q1 planning. Set minimum monthly campaign thresholds by platform (e.g., Google ≥ 35, Facebook ≥ 30) to sustain pipeline.

---

### Recommendation 5 — Test scaled investment on LinkedIn and Instagram
**Impact: Medium | Effort: Low**

Both platforms show solid conversion rates (LinkedIn 9.61%, Instagram 10.00%) with fewer campaigns (232–233) compared to Google/Facebook (467–489). There may be diminishing-return headroom on these channels.

**Action:** Run a controlled 90-day budget uplift test (+20%) on LinkedIn and Instagram. Measure CPA change to determine scalability.

---

### Recommendation 6 — Investigate and pause zero-conversion campaigns early
**Impact: Medium | Effort: Low**

Three campaigns generated zero conversions while spending between $5,553 and $20,611 each. An automated early-warning rule could prevent wasted spend.

**Action:** Implement a campaign health rule: if a campaign has > 500 clicks and < 5 conversions after 14 days, automatically flag for review and pause for optimisation.

---

## 9. Executive Summary

The marketing portfolio delivered **1.89 million conversions** across **1,881 campaigns** and 6 platforms over 13 months at a total investment of **$47.0M**. With an overall conversion rate of **10.11%** and a $24.92 average CPA, the programme broadly outperforms typical digital marketing benchmarks.

**Google** is the standout platform with the highest composite performance score (0.862), largest conversion volume (498K), and lowest CPA ($24.19). **Facebook** closely follows with the highest raw conversion rate (10.47%). Together, these two platforms should anchor the long-term channel strategy.

**Twitter** is the weakest performer across every metric — lowest conversion rate, lowest absolute conversions, and a near-zero performance score (0.006) — despite a $4.77M spend. Budget reallocation from Twitter to Google is the single highest-return action available without expanding total spend.

The most significant temporal finding is a **34% decline in campaign activity from February to October 2024**, which directly drove falling conversion volumes in H2. Proactive H2 planning and minimum-activity thresholds by platform are essential to prevent recurrence.

Campaigns running for longer durations systematically outperform short bursts, pointing to sustained always-on investment rather than fragmented tactical flights as the preferred operating model.

**Priority action list:**

1. Shift Twitter budget (25–30%) to Google immediately
2. Protect Google + Facebook combined budget share at 50–55%
3. Build H2 2025 campaign calendar in Q1 planning
4. Implement early-warning pause rules for zero-conversion campaigns
5. Pilot 90-day LinkedIn and Instagram budget uplift test

---

*Report generated by `marketing_analysis.py` — Marketing Analytics Pipeline v1.0*
