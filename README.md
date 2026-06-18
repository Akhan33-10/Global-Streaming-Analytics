# Streaming Content Discovery Dashboard

A Netflix-style interactive Power BI dashboard analyzing 500,000 viewing
records across 8 major streaming platforms from 2010 to 2024.

---

## Dashboard Preview

### Page 1 — Home
![Home Page](Screenshot_2026-06-17_150353.png)

### Page 2 — Platform Selection
![Platform Page](Screenshot_2026-06-17_150418.png)

### Page 3 — Insights
![Insights Page](Screenshot_2026-06-17_150438.png)

---

## Project Overview

This project simulates a real streaming analytics tool where users can:
- Browse all major streaming platforms
- Discover top content by category, genre, language and year
- Analyze viewing trends from 2010 to 2024
- Compare platform performance across regions

Built with a real database backend (PostgreSQL) and app-like navigation
using Power BI bookmarks and page navigation buttons.

---

## Dashboard Navigation

Home Page
"What do you want to watch today?"
Click Explore Now
↓
Platform Page
Choose from 8 streaming platforms
Each showing titles, rating and views
Click any platform logo
↓
Insights Page
Filter by Category, Year, Language, Genre
View Top 10 titles, trends and rating distribution

---

## Tools & Technologies

- Python (Pandas, NumPy) — Dataset generation with realistic correlations
- PostgreSQL 18 — Data storage and relational database design
- pgAdmin 4 — Database management and SQL queries
- Power BI Desktop — Interactive dashboard and visualizations
- DAX — Custom measures and dynamic titles

---

## Dataset Overview

### Table 1 — Content Master
- 860 unique titles (460 real + 400 realistic fictional)
- Real titles include: Stranger Things, The Boys, Game of Thrones,
  Ted Lasso, Scam 1992, IPL 2023, Squid Game and more
- Columns: content_id, title, category, genre, language,
  release_year, country_of_origin, imdb_rating, duration_minutes,
  platform, is_original

### Table 2 — Viewing Records
- 500,000 viewing records
- Columns: view_id, content_id, platform, region,
  view_year, view_month, views_millions, popularity_score, trending_rank

### Relationship
content_master[content_id] → viewing_records[content_id]
One to Many

---

## Platform Coverage

Platform       | Titles | Avg Rating | Total Views
Netflix        | 182    | 7.07       | 964M
Amazon Prime   | 115    | 7.01       | 442M
Disney+        | 96     | 7.20       | 456M
HBO Max        | 96     | 7.28       | 447M
Apple TV+      | 84     | 7.15       | 380M
Hotstar        | 103    | 7.45       | 620M
JioCinema      | 105    | 7.38       | 590M
Hulu           | 79     | 7.10       | 350M

---

## Categories Covered

- Movies
- Web Series
- Documentary
- Sports
- Kids & Animation
- Stand-up Comedy

---

## Regions Covered

- North America
- Europe
- Asia Pacific
- Latin America
- Middle East & Africa

---

## Languages Covered

English, Hindi, Spanish, French, Japanese, Korean, Arabic

---

## Key Insights

1. Sports has highest avg views at 11.76M — driven by IPL and FIFA
2. Hotstar and JioCinema dominate Asia Pacific region
3. Streaming views grew from 36M in 2010 to 1.9B in 2024
4. COVID-19 (2020) caused a massive spike in streaming viewership
5. Disney+ and Apple TV+ launched in 2019 — visible in trend chart
6. Web Series generates 9.23M avg views — second only to Sports
7. Marco Polo is Netflix top viewed title with highest engagement

---

## Realistic Correlations Built Into Dataset

- Sports content — JioCinema and Hotstar dominant
- Kids content — Disney+ dominant
- Stand-up Comedy — Netflix and Amazon Prime dominant
- Asian content — Hotstar, JioCinema, Asia Pacific region
- Platform launch years respected
- Higher IMDB rating = more views
- Recent content = more views
- Region matches platform strength

---

## DAX Measures

Total_Titles = DISTINCTCOUNT('public content_master'[title])

Total_Views = SUM('public viewing_records'[views_millions])

Avg_Rating = AVERAGE('public content_master'[imdb_rating])

Avg_Popularity = AVERAGE('public viewing_records'[popularity_score])

Insight_Title =
SELECTEDVALUE('public content_master'[category], "All Categories") &
" | " &
SELECTEDVALUE('public content_master'[platform], "All Platforms") &
" — Top Content"

Top10_Rank =
RANKX(
    ALLSELECTED('public content_master'[title]),
    [Total_Views],
    ,
    DESC,
    DENSE
)

---

## Dashboard Features

- App-like navigation — no visible page tabs
- Dynamic title changes based on platform and category selection
- Bookmarks for platform filtering
- Top 10 titles using DAX RANKX function
- Exponential viewing trend 2010-2024
- Category breakdown donut chart
- Rating distribution column chart
- 4 dropdown slicers — Category, Year, Language, Genre
- Back navigation buttons on every page
- Dark streaming theme throughout

---

## Yearly Viewing Trend

Year  | Total Views
2010  | 36M
2013  | 610M
2016  | 7,905M
2019  | 66,564M
2020  | 152,048M (COVID spike)
2022  | 564,612M
2024  | 1,902,329M

---

## Files in Repository

File                      | Description
Streaming_Dashboard.pbix  | Power BI dashboard file
content_master.csv        | 860 content titles dataset
viewing_records.csv       | 500K viewing records dataset
README.md                 | Project documentation

---

## How to Use

1. Clone this repository
2. Import CSVs into PostgreSQL
3. Connect Power BI to PostgreSQL streaming_db
4. Open Streaming_Dashboard.pbix
5. Refresh data
6. Navigate from Home page using buttons

---

## Note

This dashboard was built as part of my data analytics learning journey.
The dataset was synthetically generated using Python with realistic
correlations to simulate real-world streaming platform behavior.
Real content titles are used for authenticity but viewing data is simulated.

---

## Author

Anas Khan
GitHub: github.com/Akhan33-10
LinkedIn: linkedin.com/in/anas-khan-285415403
