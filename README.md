<div align="center">

# 🏁 F1 Race Intelligence

### Formula 1 race results, explored through Tableau

An interactive data analytics course project exploring team and driver points, non-finishes, weather, tyre compounds, and circuit types.

<p>
  <a href="https://public.tableau.com/app/profile/harsh.bhadrawale/viz/F1RaceIntelligencedashboard/Dashboard1?publish=yes"><strong>Open Tableau Dashboard</strong></a>
  &nbsp; · &nbsp;
  <a href="https://public.tableau.com/app/profile/harsh.bhadrawale/viz/F1RaceIntelligencedashboard/Story1?publish=yes"><strong>Explore Tableau Story</strong></a>
</p>

<p>
  <img alt="Seasons covered: 2010–2026" src="https://img.shields.io/badge/Seasons-2010%E2%80%932026-e10600?style=for-the-badge">
  <img alt="Race-result rows: 6464" src="https://img.shields.io/badge/Race%20results-6%2C464-222222?style=for-the-badge">
  <img alt="Tableau visualizations: 9" src="https://img.shields.io/badge/Tableau%20views-9-00a1e4?style=for-the-badge">
</p>

</div>

---

## About the project

Formula 1 results contain a lot of information about drivers, constructors, seasons, circuits, and race conditions. This project brings selected summaries together in Tableau so a student, fan, or analyst can compare patterns in one place.

The analysis is **descriptive**. It summarizes the supplied course dataset; it does not predict race outcomes or prove that weather, tyre choice, or another factor caused a result.

## Tableau views

The workbook contains a dashboard and a nine-scene Tableau Story:

| # | View | What it shows |
|---:|---|---|
| 1 | Team Points by Season | Team points across the selected seasons |
| 2 | Driver Points Leaderboard | Driver points totals, ranked |
| 3 | Non-finishes by Reason | Recorded DNF flags by reason |
| 4 | Non-finish Rate by Weather | Average DNF flag by weather category |
| 5 | Team Points Leaderboard | Constructor points totals, ranked |
| 6 | Average Positions Gained by Team | Mean positions gained by team |
| 7 | Starting Tyre Distribution | Race-record count by starting compound |
| 8 | Race Points by Circuit Type | Points totals by circuit category |
| 9 | Average Finish Position by Team | Mean finish position by team |

## Data source and scope

The course-provided workbook, `F1 Racing Project Dataset.xlsx`, contains five sheets: `race_results`, `circuits`, `championship_standings`, `lap_intelligence`, and `qualifying_results`. This Tableau project uses the `race_results` sheet, which has **6,464 rows** in the supplied copy and covers the displayed seasons **2010–2026**.

The source workbook is not included here because redistribution permission for the course resource has not been confirmed. Use the file provided through your course. The other four sheets are not joined into the current dashboard. Validate country and circuit totals against a trusted race calendar before treating them as hosted Grand Prix counts.

## Method at a glance

- **Points:** Sum of `Points` by driver, team, season, or circuit type.
- **Non-finish rate:** Average of the 0/1 `Dnf` field by weather category.
- **Positions:** Average of the positions-gained and finish-position fields by team.
- **Tyres:** Count of race records grouped by starting compound.
- **Missing finishes:** Non-finish rows are retained for DNF analysis; their finish position may be blank.
- **Historical comparison:** Points are shown as recorded in the supplied workbook, not recalculated using one modern scoring system.

See the [step-by-step project report](docs/project-report.md) for the problem statement, requirements, reference review, preparation notes, performance-testing record, and limitations.

## Project website

This repository also contains a responsive landing page that embeds the Tableau Story and links to the full dashboard. Open [`index.html`](index.html) in a browser to preview it locally; the Tableau embed needs an internet connection.

After enabling GitHub Pages, the website will be available at:

**https://hb-codes11.github.io/Race-Intelligence-F1-Dashboard-/**

The repository is configured to publish with GitHub Actions. The first deployment may take a few minutes after Pages is enabled.

## Repository contents

```text
.
├── .github/workflows/pages.yml   # Deploys the static site to GitHub Pages
├── docs/project-report.md        # Project documentation
├── index.html                    # Landing page and Tableau Story embed
├── styles.css                    # Responsive styling
├── .gitignore                    # Excludes local data/workbook files
└── README.md
```

## Recreate the Tableau workbook

1. Get the workbook from the authorized course source.
2. In Tableau Public, connect to the Excel workbook and select `race_results`.
3. Create the nine views listed above using the aggregations in **Method at a glance**.
4. Assemble the views into a dashboard and a nine-point story with captions.
5. Publish to Tableau Public and update the Dashboard and Story links in this README and `index.html` if their URLs change.

## Performance record

The Tableau workbook uses 6,464 race-result rows, nine worksheet views, one dashboard, and nine story scenes. No custom calculated fields were needed for the documented views; the charts use Tableau aggregations of source fields. Rendering times have not been measured on a controlled device and network, so this repository makes no load-time claim. Filter scope and dashboard-wide propagation should be recorded if performance testing is completed.

## References

- Tableau, [Stories](https://help.tableau.com/current/pro/desktop/en-us/stories.htm)
- Tableau, [Creating a Story](https://help.tableau.com/current/pro/desktop/en-us/story_create.htm)
- Formula 1, [The beginner’s guide to the F1 Drivers’ Championship](https://www.formula1.com/en/latest/article/the-beginners-guide-to-the-f1-drivers-championship.53MjXJzTDxQnfxfoCLnxNZ)
- Formula 1, [The beginner’s guide to the Formula 1 weekend](https://www.formula1.com/en/latest/article/the-beginners-guide-to-the-formula-1-weekend.5RFZzGXNhEi9AEuMXwo987)

## Author

**Harsh Bhadrawale** · Data Analytics with Tableau course project
