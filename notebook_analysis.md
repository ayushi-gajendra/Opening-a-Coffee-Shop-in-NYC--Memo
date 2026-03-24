# 🐍 Notebook Analysis — Opening a Coffee Shop in NYC

> **File:** `C5M1_Assignment.ipynb`  
> **Purpose:** Coworker's completed analysis — your job is to read, understand, and turn it into a memo  
> **Note:** The notebook lacks narrative and structure — it's a great example of *what not to share* with non-technical stakeholders.

---

## ⚠️ What's Wrong With This Notebook (as a Storytelling Artifact)

The coworker's notebook is useful for analysis but **not ready to share** as a data storytelling artifact because:
- No narrative context explaining *why* each analysis was done
- No clear main conclusion at the top
- Code cells mixed with sparse markdown — non-technical readers see clutter
- Results are not connected to business implications
- No recommendations section

> This is why you're being asked to write a **memo** instead of sharing the notebook directly.

---

## 📊 Section 1: Data Setup

### What the code does:
```python
import pandas as pd, matplotlib.pyplot as plt, seaborn as sns, sqlite3
conn = sqlite3.connect("restaurant_data.db")

query = """
SELECT DISTINCT inspections.*, ratings.rating, ratings.price_level,
       ratings.total_reviews, ratings.types
FROM inspections LEFT JOIN ratings 
ON inspections.NAME = ratings.name AND inspections.ZIPCODE = ratings.zip_code 
WHERE inspections.CUISINE_DESCRIPTION LIKE '%coffee%'
"""
coffeeshops_joined = pd.read_sql_query(query, conn)
```

### What this means:
- Pulls all records from an NYC restaurant inspections database joined with customer rating data
- Filters only coffee/tea establishments
- The join combines **official health inspection data** with **customer-facing review data** (like Google Maps ratings)

**Raw dataset shape:** `(4273, 31)` — 4,273 inspection records across 31 columns

> Each restaurant can appear multiple times (one row per inspection date). The next step deduplicates this.

```python
# Keep only the LAST inspection for each restaurant
coffeeshops_last_inspection = coffeeshops_joined.drop_duplicates(subset='CAMIS', keep='last')
```

**After deduplication:** `1,004 unique coffee shops` across NYC

---

## 📊 Section 2: Competition by Borough

### Code:
```python
coffeeshops_by_borough = coffeeshops_last_inspection.groupby("BORO")
coffeeshops_by_borough.size()
```

### Output:
```
BORO
Bronx             40
Brooklyn         269
Manhattan        531
Queens           146
Staten Island     18
```

### 💡 Insight:
**Manhattan is by far the most saturated market.** With 531 shops, it holds **53% of all NYC coffee shops** despite being just one of five boroughs. Staten Island (18) and the Bronx (40) have very few shops but may also have lower demand.

| Borough | Shops | % of Total | Signal |
|---|---|---|---|
| Manhattan | 531 | 52.9% | 🔴 Highly saturated |
| Brooklyn | 269 | 26.8% | 🟡 Competitive |
| Queens | 146 | 14.5% | 🟢 Opportunity zones exist |
| Bronx | 40 | 4.0% | 🟡 Low competition but lower demand |
| Staten Island | 18 | 1.8% | 🟡 Very low supply AND demand |

---

## 📊 Section 3: Grade Distribution by Borough

### Output:
```
GRADE          A       B      C       N       Z
BORO                                            
Bronx       77.4%    NaN    3.2%   19.4%    NaN
Brooklyn    84.7%    4.6%   1.9%    5.6%    3.2%
Manhattan   85.6%    4.1%   2.6%    5.0%    2.6%
Queens      87.9%    2.8%    NaN    4.7%    4.7%
Staten Isl. 77.8%   16.7%   5.6%    NaN     NaN
```

> **Grade N** = Not yet graded (often new establishments or re-inspection pending)  
> **Grade Z** = Grade pending (grade card issued but not yet official)

### 💡 Insight:
**Queens has the highest A-grade rate (87.9%)**, suggesting either better compliance or fewer complex establishments. The Bronx has an unusually high "N" rate (19.4%), which could mean more new establishments or delayed re-inspections.

---

## 📊 Section 4: Average Reviews and Rating by Borough

### Output:
```
              total_reviews    rating
BORO                                  
Bronx             330.71      4.29
Brooklyn          307.31      4.45
Manhattan         517.81      4.28
Queens            301.39      4.33
Staten Island        NaN       NaN
```

### 💡 Insight — Two competing signals in Manhattan:

| Signal | Value | Interpretation |
|---|---|---|
| Most reviews | 517.8/shop | High foot traffic, high customer engagement |
| Lowest rating | 4.28/5 | More competition = harder to stand out; customers more critical |
| Brooklyn rating | 4.45/5 | Highest satisfaction; less cutthroat competition |

> **Reviews are used as a proxy for consumer demand.** A zip code with high reviews but few shops = underserved market.

---

## 📊 Section 5: Zip Code Deep-Dive

### Key Visualization Outputs (from interactive plots):

The notebook generates 4 interactive plots per zip code showing:
1. Number of coffee shops per zip code
2. Average rating per zip code
3. Average number of reviews per zip code
4. Price level distribution

### 💡 Special Zip Code Insights:

| Zip Code | Borough | # Shops | Avg Reviews/Shop | Avg Rating | Signal |
|---|---|---|---|---|---|
| **11366** | Queens | 1 | ~1,000 | 4.7 | 🟢 **High demand, almost no competition** |
| **10026** | Manhattan | 4 | ~1,800 | 4.3 | 🟢 **Very high engagement, manageable competition** |
| 10001–10020 | Lower Manhattan | High | Moderate | Varies | 🔴 Saturated — many shops, not proportionally more reviews |

> **The core logic:** If a zip code has very few shops but very high review counts, it means there's *more consumer demand than current supply can serve*. That's a market gap.

---

## 📊 Section 6: Price Level vs. Reviews

### Code:
```python
# Statistical t-test comparing review counts at price level 1 vs price level 2
t_stat, p_value = stats.ttest_ind(price_level_1_reviews, price_level_2_reviews,
    equal_var=False, alternative='less', nan_policy='omit')
```

### Output:
```
T-statistic: -6.4634
P-value: 0.0000
```

### 💡 Insight:
- **Mid-priced shops (level 2) receive significantly more reviews** than budget shops (level 1)
- The p-value of 0.0000 means this result is **statistically highly significant** — not due to chance
- More reviews = more customer engagement = more business visibility

> In plain language: **mid-range pricing attracts more customers and drives more visibility**, not budget pricing.

---

## 📊 Section 7: Health Inspection Pass Rates

### Output (from bar chart):
- **Initial inspections: ~50% pass rate** — half of new coffee shops fail their very first inspection
- **Cycle inspections and re-inspections have much higher pass rates** — establishments typically fix issues when given a second chance

### 💡 Insight:
Failing an initial inspection doesn't close your business, but it:
- Triggers a follow-up inspection (cost and time)
- Can result in a lower grade being publicly posted
- Creates reputational risk before you've even opened properly

> **Actionable implication:** Pre-opening health code assessment is essential.

---

## 📊 Section 8: Correlation Analysis

### Three correlations computed:

#### 1. Rating vs. Inspection Score
```
Correlation: 0.065
```
**Insight:** Almost no correlation. A high health inspection score does NOT necessarily translate to high customer ratings. These measure completely different things — operational compliance vs. customer experience.

---

#### 2. Price Level vs. Inspection Score
```
Correlation: -0.081
```
**Insight:** Very weak negative relationship. Price level has almost no bearing on how well a shop does in health inspections.

---

#### 3. Rating vs. Price Level
```
Correlation: -0.315
```
**Insight:** **This is the most important correlation.** A moderate negative correlation means that **lower-priced shops tend to receive higher customer ratings**. 

| Correlation Value | Interpretation |
|---|---|
| -0.315 | Moderate negative relationship |
| Direction | As price goes up → ratings tend to go down |
| Business implication | **Premium pricing is a risk to customer satisfaction** |

> A -0.315 correlation is not overwhelming, but it's consistent enough to be actionable — the data suggests customers in the NYC coffee market are price-sensitive.

---

## 🔑 Summary: All Notebook Insights

| # | Insight | Supporting Data |
|---|---|---|
| 1 | NYC has 1,004 coffee shops across 5 boroughs | `len(coffeeshops_last_inspection) = 1004` |
| 2 | Manhattan is the most saturated market | 531 shops = 53% of all NYC shops |
| 3 | Queens Zip 11366 is the top opportunity | 1 shop, ~1,000 reviews, 4.7 rating |
| 4 | Manhattan Zip 10026 is high-engagement with moderate competition | 4 shops, ~1,800 reviews/shop |
| 5 | Brooklyn has the highest customer satisfaction | Avg rating 4.45 vs 4.28 in Manhattan |
| 6 | Initial health inspections have ~50% pass rate | Bar chart output |
| 7 | Mid-priced shops attract more engagement | t-stat: -6.46, p-value: 0.0000 |
| 8 | Lower prices correlate with higher ratings | Correlation: -0.315 |
| 9 | Health scores and customer ratings are unrelated | Correlation: +0.065 |
