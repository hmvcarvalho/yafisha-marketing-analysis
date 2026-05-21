# Y.Afisha Marketing Analysis

Marketing spend optimization analysis for Y.Afisha. Covers product metrics (DAU/MAU/WAU), cohort retention, conversion timing, LTV, CAC and ROI by acquisition source — with actionable recommendations.

## About Y.Afisha

Y.Afisha is a ticket sales platform for events such as concerts, theatre, and cinema. This analysis focuses on understanding how users interact with the platform, when and how much they spend, and which marketing channels drive the most valuable customers.

## Dataset

| File | Description | Period |
|---|---|---|
| `visits_log_us.csv` | Website sessions | Jan 2017 – Dec 2018 |
| `orders_log_us.csv` | Completed orders | Jan 2017 – Dec 2018 |
| `costs_us.csv` | Marketing spend by source | Jan 2017 – Dec 2018 |

After optimization, datasets were reduced by 70–87% in memory usage via dtype conversion and datetime parsing.

## Analysis Structure

### 1. Data Loading and Preparation
- Loaded all three datasets with optimized dtypes (`category`, `datetime`)
- Standardized column names to `snake_case`
- Checked and confirmed no duplicates or null values across datasets

### 2. Product Analysis
- **DAU / WAU / MAU** — steady growth from Jun to Dec 2017, peaking in December; MAU approximately tripled over this period
- **Sessions per day** — closely mirrors DAU; most users generate one session per day
- **Session duration** — right-skewed; median ~6 minutes after filtering negative-duration records and the top 1% outliers
- **User retention** — sharp drop after week 1, stabilizing at a low level by week 4; typical for a purchase-intent platform

### 3. Sales Analysis
- **Time to first purchase** — over 50% of converting users purchase on day 0; 75% within 2 days
- **Orders per user** — heavily right-skewed; most users place 1–2 orders; older cohorts accumulate more orders due to observation window
- **Average purchase value** — stable at ~3.4 to 4.7 after outlier removal; no upward trend
- **LTV by cohort** — June 2017 cohort has highest avg LTV (~9.4); newer cohorts trend lower due to less time in the dataset

### 4. Costs Analysis

**Total marketing spend: ~329,131**

| Source | Total Users | Total Costs | Avg CAC |
|---|---|---|---|
| 4 | 72,346 | 61,073 | 0.89 |
| 9 | 6,448 | 5,517 | 0.90 |
| 10 | 6,903 | 5,822 | 0.91 |
| 5 | 49,237 | 51,757 | 1.05 |
| 3 | 66,116 | 141,321 | 2.14 |
| 1 | 9,469 | 20,800+ | 2.20 |

- **Source 3** accounts for ~43% of total spend but shows consistently negative or near-zero ROI
- **Source 1** has the highest ROI across cohorts (peak 5.16 in Jun 2017) despite a moderate CAC
- Marketing spend grew from ~18K/month (Jun 2017) to a peak of ~38K/month (Dec 2017), aligning with DAU growth

### 5. Conclusions and Recommendations

| Action | Rationale |
|---|---|
| Increase investment in **Source 1** | Consistently highest ROI across cohorts |
| Reduce investment in **Source 3** | Largest spend (~43%) with near-zero or negative ROI |
| Monitor **Source 4** | Lowest CAC (0.89) and highest user volume — strong candidate if LTV improves |
| Evaluate investment over **6-month horizon** | Short-term ROI systematically undervalues channels with loyal repeat buyers |
| Investigate **Sources 9 and 10** | Low CAC, limited scale — worth testing for volume expansion |

## Setup

```bash
python -m venv .venv
```

**Activate the virtual environment:**

- Windows: `.venv\Scripts\activate`
- macOS/Linux: `source .venv/bin/activate`

```bash
pip install -r requirements.txt
```

## Dependencies

```
pandas
numpy
matplotlib
seaborn
scipy
ipykernel
```
