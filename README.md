<div align="center">

# 🏁 F1 Race Intelligence

### A Tableau project on Formula 1 race results

[View Dashboard](https://public.tableau.com/app/profile/harsh.bhadrawale/viz/F1RaceIntelligencedashboard/Dashboard1) · [Explore Story](https://public.tableau.com/app/profile/harsh.bhadrawale/viz/F1RaceIntelligencedashboard/Story1) · [Project Website](https://hb-codes11.github.io/Race-Intelligence-F1-Dashboard-/)

**6,464 race-result records · 2010–2026 in the supplied dataset · 9 Tableau views**

</div>

## Why I built this

I built this project for my **Data Analytics with Tableau** course. Having some familiarity with Formula 1 helped me connect the data to questions I could understand: how team points change across seasons, which drivers have the highest totals, and how non-finishes are distributed across different conditions.

The result is a Tableau dashboard, a nine-scene Story, and a small website for opening the published analysis. The figures come from the course dataset; I have not independently verified every record against official F1 results.

## Explore the project

| Resource | Link |
|---|---|
| Tableau dashboard | [Open dashboard](https://public.tableau.com/app/profile/harsh.bhadrawale/viz/F1RaceIntelligencedashboard/Dashboard1) |
| Tableau Story | [Open nine-scene Story](https://public.tableau.com/app/profile/harsh.bhadrawale/viz/F1RaceIntelligencedashboard/Story1) |
| Website | [Open project website](https://hb-codes11.github.io/Race-Intelligence-F1-Dashboard-/) |
| Documentation | [Read the development report](docs/project-report.md) |

## Dataset

The course provided an Excel workbook named `F1 Racing Project Dataset.xlsx`. It contains five sheets:

- `race_results`
- `circuits`
- `championship_standings`
- `lap_intelligence`
- `qualifying_results`

I used **`race_results`**, which showed **6,464 rows** in Tableau. Its season values range from **2010 to 2026**. The other sheets were not joined to this analysis.

The Excel file and local Tableau workbook are not included in this repository. To recreate the analysis, use the dataset supplied by the course.

## What the charts show

| View | Measure used | Purpose |
|---|---|---|
| Team Points by Season | Sum of points by season and team | Compare how each team's recorded points change over time |
| Driver Points Leaderboard | Sum of points by driver | Rank drivers by their points in the dataset |
| DNF by Reason | Sum of the DNF flag by reason | Compare recorded reasons for non-finishes |
| DNF by Weather | Average of the DNF flag by weather | Compare the proportion of records marked as DNF |
| Team Points Leaderboard | Sum of points by team | Compare team totals |
| Average Positions Gained by Team | Average positions gained | Compare movement from starting to finishing positions |
| Starting Tyre Distribution | Count of records by starting compound | Compare how often each starting compound appears |
| Race Points by Circuit Type | Sum of points by circuit type | Compare totals across circuit categories |
| Average Finish Position by Team | Average finish position | Compare mean finishing positions |

The dashboard puts these views together. The Story presents them as separate scenes with captions.

## How I developed it

1. Connected the Excel workbook to Tableau Public and opened `race_results`.
2. Reviewed the available fields, row count, and season range.
3. Changed Season from a summed measure to a dimension for the trend chart.
4. Used sums for points, averages for the position measures, and counts for starting tyres.
5. Kept DNF records for the non-finish charts and added relevant Season and DNF Reason filters.
6. Built the worksheets, assembled the dashboard, and added the Story captions.
7. Published the workbook to Tableau Public.
8. Created the website and deployed it through GitHub Pages.

The [project report](docs/project-report.md) explains the problem, chart choices, development steps, and current limitations in more detail.

## Reading the results

A few details matter when interpreting the charts:

- **6,464 is a count of result records, not a count of Grand Prix events.**
- Driver and team totals describe the supplied records. They should not be presented as verified career statistics.
- A higher points total for one circuit category can reflect more records in that category.
- The weather chart shows an association with DNF flags. It does not establish the cause of a non-finish.
- Average finish position depends on the records with a valid finish value.
- Points are used as supplied, without adjusting historical seasons to a common scoring system.

## Website and deployment

The website uses HTML and CSS and embeds the published Tableau Story. It requires an internet connection to load the visualization.

GitHub Pages is configured to use **GitHub Actions**. Changes pushed to `main` trigger the deployment workflow.

To open the website locally, download the repository and open `index.html` in a browser.

## Repository structure

```text
.
├── .github/workflows/pages.yml   # GitHub Pages deployment
├── docs/project-report.md        # Detailed project documentation
├── index.html                    # Website and Tableau embed
├── styles.css                    # Website styling
├── .gitignore
└── README.md
```

## Performance notes

The documented workbook has nine worksheet views, one dashboard, and nine Story scenes. The charts use aggregations of source fields rather than custom calculated fields.

Loading times have not been measured in a controlled test, and dashboard-wide filter behaviour has not been fully checked. Those checks remain separate from publishing the project.

## References

- [Tableau: Stories](https://help.tableau.com/current/pro/desktop/en-us/stories.htm)
- [Tableau: Create a Story](https://help.tableau.com/current/pro/desktop/en-us/story_create.htm)
- [Formula 1: Beginner's guide to the Drivers' Championship](https://www.formula1.com/en/latest/article/the-beginners-guide-to-the-f1-drivers-championship.53MjXJzTDxQnfxfoCLnxNZ)
- [Formula 1: Beginner's guide to a race weekend](https://www.formula1.com/en/latest/article/the-beginners-guide-to-the-formula-1-weekend.5RFZzGXNhEi9AEuMXwo987)

**Harsh Bhadrawale**  
Data Analytics with Tableau — course project
