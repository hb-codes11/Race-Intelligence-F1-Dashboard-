# F1 Race Intelligence Dashboard

An educational Tableau project exploring Formula 1 race results through interactive charts, a dashboard, and a nine-scene story.

## View the project

- **Tableau Public story:** [Open the dashboard story](https://public.tableau.com/app/profile/harsh.bhadrawale/viz/F1RaceIntelligencedashboard/Story1?publish=yes)
- **Project website:** [Open the GitHub Pages site](https://hb-codes11.github.io/Race-Intelligence-F1-Dashboard-/) *(available after GitHub Pages finishes its first deployment)*

## Project question

How can historical race-result data help viewers compare driver and team points, non-finishes, weather categories, tyre compounds, and circuit types? The project is descriptive: it summarizes the supplied dataset and does not predict race outcomes or establish causal relationships.

## What is included

- Tableau Public dashboard and story link
- A responsive project landing page with the Tableau story embedded
- Nine Tableau visualizations covering:
  1. Team points by season
  2. Driver points leaderboard
  3. Non-finishes by reason
  4. Non-finish rate by weather
  5. Team points leaderboard
  6. Average positions gained by team
  7. Starting tyre distribution
  8. Race points by circuit type
  9. Average finish position by team
- [Step-by-step project report](docs/project-report.md)

## Data

The course-provided workbook is named `F1 Racing Project Dataset.xlsx`. It has five sheets: `race_results`, `circuits`, `championship_standings`, `lap_intelligence`, and `qualifying_results`. This Tableau project uses the `race_results` sheet, which contains 6,464 records in the supplied copy. The workbook screenshots show seasons from 2010 through 2026.

The Excel file is not included in this repository because it is a course-provided resource and redistribution permission has not been confirmed. Use the copy provided by your course. Country and circuit counts should be independently validated before being reported as historical Grand Prix totals.

## Recreate it

1. Open Tableau Public and connect to the authorized course workbook.
2. Select `race_results` as the data source.
3. Create the nine worksheets listed above. See the project report for the field and aggregation guide.
4. Assemble the worksheets into a dashboard and arrange them as nine story points.
5. Publish the workbook to Tableau Public. Update the links in `README.md` and `index.html` if Tableau gives you a different URL.

## Run the project website locally

Open `index.html` in a browser. It is a static site and needs no install or build step. The embedded Tableau story requires an internet connection; use the Tableau Public link if embedding is blocked by browser settings.

## Publish the website with GitHub Pages

The repository includes a GitHub Actions workflow for GitHub Pages. In the repository, open **Settings → Pages**, set the build and deployment source to **GitHub Actions**, then push to `main`. The workflow publishes the root folder; the site URL is shown in the Pages settings after deployment.

## Project status

The Tableau workbook is published. Rendering timings and device-specific performance measurements have not yet been recorded; see the report for the current performance-testing notes and limitations.

## Author

Harsh Bhadrawale · Data Analytics with Tableau course project
