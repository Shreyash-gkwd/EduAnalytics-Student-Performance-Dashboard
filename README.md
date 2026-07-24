# EduAnalytics — Student Performance Analytics Dashboard

A data analytics project that analyzes student academic and engagement data to identify performance trends and flag at-risk students, using **Python** for data processing and **Power BI** for interactive visualization.

## Overview

This project analyzes student academic datasets — attendance, grades, and engagement metrics (participation, resource usage, discussion activity) — to:
- Identify performance trends across students, subjects, semesters, and grade levels
- Building an interactive dashboard for class-wise and student-wise monitoring
- Flag at-risk students using rule-based logic on attendance and engagement patterns
- Presenting findings in a clear, easy-to-understand visual format

## Dataset

**Students' Academic Performance Dataset (xAPI-Edu-Data)**
Source: [Kaggle](https://www.kaggle.com/datasets/aljarah/xAPI-Edu-Data)

480 student records with 17 features collected from the Kalboard 360 learning management system via the Experience API (xAPI), including demographic info, academic background (grade, section, subject, semester), behavioral/engagement metrics, and final performance class.

## Tech Stack

- **Python** — Pandas, NumPy (data cleaning, feature engineering, trend analysis)
- **Power BI** — interactive dashboard and visualizations

## Project Workflow

1. **Data Loading & Cleaning** — loaded the raw CSV, checked for missing values, standardized column names
2. **Feature Engineering**
   - `EngagementScore` — combined average of raised-hands, resources visited, announcements viewed, and discussion participation (0–100 scale)
   - `AttendanceRisk` — binary flag derived from `StudentAbsenceDays`
   - `PerformanceProxy` — numeric proxy mapped from performance class (Low / Medium / High)
3. **Trend Analysis** — aggregated engagement and performance by subject, semester, and grade level to surface patterns
4. **At-Risk Flagging** — rule-based logic: a student is flagged **At Risk** if they have high absences (>7 days), below-median engagement, and are not already a high performer
5. **Export** — cleaned, feature-engineered dataset exported to CSV for Power BI
6. **Dashboard** — built an interactive Power BI report with KPI cards, subject/semester trend charts, an engagement-vs-performance scatter plot, an at-risk student watchlist table, and slicers for filtering by gender, topic, semester, and grade

## Repository Contents

| File | Description |
|---|---|
| `EduAnalytics.ipynb` | Jupyter Notebook containing data cleaning, feature engineering, trend analysis, and data export |
| `edu_analytics_processed.csv` | Cleaned, feature-engineered dataset used as the Power BI data source |
| `Student Performance Dashboard.pbix` | Power BI dashboard file |
| `Dashboard_images/` | Dashboard preview images |

## How to Run

1. Download `xAPI-Edu-Data.csv` from the [Kaggle dataset page](https://www.kaggle.com/datasets/aljarah/xAPI-Edu-Data) and place it in the project folder.
2. Install dependencies:
   ```bash
   pip install pandas numpy
   ```
3. Open `EduAnalytics.ipynb` in Jupyter Notebook or JupyterLab and run all cells sequentially.
   This prints subject/semester/grade-level trends and at-risk summary to the console, and exports `edu_analytics_processed.csv`.
4. Open `Student Performance Dashboard.pbix` in Power BI Desktop, or load `edu_analytics_processed.csv` into a new Power BI report.

## Dashboard Preview

<img src="images/dashboard_overview.png" width="900"/>

## Key Insights

- Approximately 31% of students were identified as **At Risk** based on attendance and engagement criteria.
- Higher student engagement was generally associated with better academic performance.
- Performance varied across subjects, highlighting areas where additional academic support may be beneficial.
- Students with frequent absences (>7 days) were more likely to fall into the at-risk category.
- Interactive slicers allow users to analyze trends by gender, semester, topic, and grade level.

## Future Improvements

- Integrate real-time student data through an LMS or database connection.
- Replace rule-based at-risk flagging with a machine learning classification model
- Add time-series tracking if multi-semester longitudinal data becomes available
- Build automated alerts/reports for flagged students

## Author

Shreyash S. Gaikwad

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/shreyash-gaikwad-66154a286)
