# Olympic Games Analytics Dashboard

> An interactive data analytics web application for exploring 120+ years of Summer Olympic Games history — built with Python, Streamlit, and Plotly.

---

## Problem Statement

Historical Olympic data spanning 134,000+ athlete records across 35+ Games is rich with insights — but buried in raw CSVs. Sports analysts, journalists, and curious fans have no quick way to answer questions like:
- Which country dominated a specific decade?
- How has female athlete participation grown since 1900?
- What does the age distribution of Gold medalists look like across sports?

This dashboard solves that by turning raw data into an interactive, self-service analytics experience.

---

## Solution Overview

A full-stack data web app that ingests, preprocesses, and visualizes Olympic athlete data in real time. Users select views from a sidebar (Medal Tally, Overall Analysis, Country-wise Analysis, Athlete-wise Analysis) and the app dynamically renders the relevant charts, tables, and KPIs.

---

## Key Features

| Feature | Description |
|---|---|
| Medal Tally | Filter by year and country to view Gold/Silver/Bronze totals |
| Participation Trends | Line charts showing nations, events, and athletes over time |
| Country Analysis | Per-country medal trends, sport heatmaps, and top athletes |
| Athlete Analysis | Age distributions by medal type, Height vs. Weight scatter plots |
| Gender Trends | Men vs. Women participation over time (1896-2016) |
| Sport Heatmap | Events-per-sport frequency over each Olympic year |

---

## Tech Stack

| Layer | Tools |
|---|---|
| Frontend/UI | Streamlit |
| Data Processing | Pandas, NumPy |
| Visualizations | Plotly Express, Plotly Figure Factory, Seaborn, Matplotlib |
| Statistical Analysis | SciPy |
| Language | Python 3.x |
| Data | athlete_events.csv, noc_regions.csv (120+ years, 134K+ records) |

---

## Architecture & Workflow

```
Raw CSV Data
    |
    v
preprocessor.py  <-- ETL Pipeline
 * Filter Summer Olympics
 * Merge NOC region mappings
 * Deduplicate records
 * One-hot encode Medal column
    |
    v
helper.py  <-- Business Logic Layer
 * Medal aggregation (by year/country)
 * Time-series (nations/events/athletes over time)
 * Country-level heatmap pivots
 * Athlete statistics & rankings
 * Gender participation analysis
    |
    v
app.py  <-- Presentation Layer (Streamlit)
 * Sidebar navigation & filters
 * Dynamic chart rendering (Plotly, Seaborn)
 * KPI metric cards
 * Interactive data tables
```

---

## How It Works

1. On app launch, both CSVs are loaded and passed through `preprocessor.preprocess()` — filtering for Summer Games, merging country regions, and encoding medal columns.
2. The Streamlit sidebar lets users pick from four analysis modes.
3. Each mode calls specific `helper.py` functions that filter and aggregate data on demand.
4. Results are rendered as interactive Plotly charts or Seaborn/Matplotlib heatmaps embedded in the Streamlit layout.

---

## Setup Instructions

```bash
# Clone the repository
git clone https://github.com/NeheMalviya1243/olympic-games-analytics-dashboard.git
cd olympic-games-analytics-dashboard

# Install dependencies
pip install -r requirements.txt

# Place your data files in the project root:
# - athlete_events.csv
# - noc_regions.csv

# Run the app
streamlit run app.py
```

---

## Example Use Case

**Scenario:** A sports journalist wants to compare USA vs. China medal performance since 1984.
1. Select **Country-wise Analysis** from the sidebar
2. Choose **United States** to view medal tally trend + sport heatmap
3. Switch to **China** to compare trends side-by-side
4. Use **Athlete-wise Analysis** to compare age profiles of medalists by sport

---

## Screenshots / Demo

> Add screenshots here after running the app locally

| Dashboard View | Preview |
|---|---|
| Medal Tally | `[screenshot]` |
| Participation Trends | `[screenshot]` |
| Country Heatmap | `[screenshot]` |
| Athlete Age Distribution | `[screenshot]` |

---

## Project Structure

```
olympic-games-analytics-dashboard/
n-- app.py              # Streamlit UI & navigation
n-- helper.py           # Data aggregation & business logic
n-- preprocessor.py     # ETL pipeline
n-- requirements.txt    # Python dependencies
n-- athlete_events.csv  # Primary dataset (134K+ rows) - add locally
n-- noc_regions.csv     # Country/NOC mapping - add locally
n-- README.md
```

---

## Future Improvements

- [ ] Add Winter Olympics data for full comparison
- [ ] Deploy to Streamlit Cloud for public access
- [ ] Add predictive modeling to forecast medal counts for future Games
- [ ] Integrate real-time data via an Olympic API
- [ ] Add drill-down to individual athlete career pages
- [ ] Export filtered results as CSV/PDF reports

---

## Recruiter Highlights

- **Scale:** Analyzed 134,000+ athlete records across 35 Olympic Games (1896-2016)
- **End-to-End:** Built a complete data pipeline from raw CSV ingestion to interactive visualization
- **Multiple Views:** 4 distinct analysis modules (Medal Tally, Overall, Country, Athlete)
- **Production Patterns:** Separated ETL (preprocessor.py), business logic (helper.py), and UI (app.py) following software engineering best practices
- **Business Value:** Demonstrates ability to translate raw data into actionable, stakeholder-ready insights

---

*Built by [Nehe Malviya](https://github.com/NeheMalviya1243) | Rider University — Business Data Analytics*
