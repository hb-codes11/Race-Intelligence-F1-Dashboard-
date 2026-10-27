# Formula 1 Race Intelligence Dashboard — Project Report

**Author:** Harsh Bhadrawale  
**Course:** Data Analytics with Tableau  
**Published story:** [Tableau Public](https://public.tableau.com/app/profile/harsh.bhadrawale/viz/F1RaceIntelligencedashboard/Story1?publish=yes)

## 1. Problem understanding

Formula 1 race-result workbooks contain many records and fields. A reader who wants to compare season and team points, driver totals, non-finishes, weather labels, tyre compounds, and circuit categories needs to move between tables or perform repeated summaries. This project uses Tableau to make those comparisons available in one dashboard and a guided story.

### Business problem

The project addresses an information-access problem: how to present historical race-result summaries in a form that a student, fan, or analyst can explore and explain quickly. The dashboard is a learning and communication aid, not a decision system for a real F1 team.

### Requirements addressed

- Connect an Excel workbook to Tableau and inspect the source sheet.
- Prepare fields and aggregations for visualization.
- Create multiple views and assemble a dashboard.
- Create a Tableau Story with nine scenes and captions.
- Publish the dashboard/story to Tableau Public.
- Document the analysis, data scope, chart logic, and limitations.
- Provide a lightweight web page that links to and embeds the public story.

## 2. Literature and reference review

Tableau describes a story as a sequence of views that can provide context and communicate a narrative; an individual view in a story is a story point. This informed the choice to arrange the project’s nine views as a sequence instead of presenting isolated charts alone. Tableau’s story guidance also recommends choosing an appropriate view or dashboard for each story point.

Formula 1’s official beginner guide explains that championship points are awarded to the leading finishers and publishes the current Grand Prix points scale. The workbook spans multiple seasons, so historical points totals in this project are treated as recorded in the supplied data; they are not recalculated under one current scoring system.

References:

- Tableau, [Stories](https://help.tableau.com/current/pro/desktop/en-us/stories.htm)
- Tableau, [Creating a Story](https://help.tableau.com/current/pro/desktop/en-us/story_create.htm)
- Formula 1, [The beginner’s guide to the F1 Drivers’ Championship](https://www.formula1.com/en/latest/article/the-beginners-guide-to-the-formula-1-drivers-championship.53MjXJzTDxQnfxfoCLnxNZ)
- Formula 1, [The beginner’s guide to the Formula 1 weekend](https://www.formula1.com/en/latest/article/the-beginners-guide-to-the-formula-1-weekend.5RFZzGXNhEi9AEuMXwo987)

## 3. Social and business impact

An accessible public dashboard can help learners and fans inspect race-result summaries and practice reading interactive visualizations. It may support classroom discussion and sports-media exploration. It should not be used to assess driver ability, make recruitment decisions, or draw causal conclusions without data validation and additional context.

## 4. Data collection and extraction

The source is the course-provided Excel workbook `F1 Racing Project Dataset.xlsx`. It has five sheets: `race_results`, `circuits`, `championship_standings`, `lap_intelligence`, and `qualifying_results`. The Tableau workbook uses `race_results`, with 6,464 records in the supplied copy. The visible season range in the project is 2010–2026.

The workbook remains outside this GitHub repository because it is course-provided and redistribution permission has not been confirmed. The repository documents how to use the authorized course copy.

## 5. Data inspection and preparation

- Connected Tableau Public to the Excel workbook and selected `race_results`.
- Inspected the field list and row count in Tableau’s data source view.
- Used the `Season` field as a season dimension for the team trend, with the displayed range 2010–2026.
- Retained DNF records for the reliability views. The supplied data has blank finish positions for some non-finish records.
- Used an average for finish position and positions gained so the charts communicate per-record means rather than sums.
- Used the average of the 0/1 `Dnf` field for the weather view, representing the share of rows flagged as non-finish within each weather category.
- Used sums for points and record counts for starting-compound distribution.

The four other sheets in the Excel workbook are not joined into the current analysis. Country/circuit totals should be checked against a trusted race calendar before being presented as counts of hosted Grands Prix.

## 6. Visualizations

The Tableau story contains nine scenes:

| Scene | Visualization | Measure / grouping |
|---|---|---|
| 1 | Team points by season | Sum of points by season and team |
| 2 | Driver points leaderboard | Sum of points by driver |
| 3 | Non-finishes by reason | DNF count/flag by DNF reason |
| 4 | Non-finish rate by weather | Average of DNF flag by weather |
| 5 | Team points leaderboard | Sum of points by team |
| 6 | Average positions gained by team | Average positions gained by team |
| 7 | Starting tyre distribution | Record count by starting compound |
| 8 | Race points by circuit type | Sum of points by circuit type |
| 9 | Average finish position by team | Average finish position by team |

These views are intended to support comparisons. Since the workbook is historical and its field definitions are inherited from the course dataset, the chart labels should be read with those definitions in mind.

## 7. Dashboard and story design

The Tableau dashboard brings the nine views together for overview and comparison. The Tableau Story presents the views in nine captioned scenes. The published story is linked above and embedded in the project website (`index.html`). A reader can open the visualization directly on Tableau Public if the embedded view is blocked by their browser.

## 8. Performance testing

**Data rendered:** 6,464 rows in the `race_results` sheet.  
**Worksheet views:** 9.  
**Dashboard:** 1.  
**Story scenes:** 9.  
**Calculated fields:** No custom calculated fields were required for the charts documented here; the views use Tableau aggregations of source fields.  
**Filters:** Season range and DNF reason selections are used in the relevant views. Dashboard-wide filter propagation was not verified.  
**Rendering timings:** Not measured on a controlled device/network; no response-time claim is made.

For a repeatable performance check, record the device, network, selected filters, and time from opening the published story to rendering each view. Compare the same set of filters and views after any workbook changes.

## 9. Publishing and web integration

The Tableau workbook/story is published to Tableau Public. This repository’s static landing page embeds the story using Tableau Public and also provides a direct link. GitHub Pages can host the static page using the included Actions workflow; it does not host the Excel workbook or Tableau data itself.

## 10. Reproduction steps

1. Obtain the course workbook from its authorized source.
2. In Tableau Public, connect to the Excel file and open `race_results`.
3. Build the nine views listed in Section 6 with the shown dimensions and aggregations.
4. Assemble the dashboard, then make a story with one scene per view and add captions.
5. Publish the Tableau workbook/story and replace the project URL if it changes.
6. Open `index.html` locally or deploy it with GitHub Pages to view the embedded story.

## 11. Limitations

- Results reflect only the supplied workbook and the fields used in `race_results`.
- The project does not verify every record against official race results.
- Historical points systems have changed; the project displays the data’s recorded points and does not normalize across eras.
- A DNF rate by weather is descriptive and does not establish that weather caused a non-finish.
- No controlled rendering-time benchmark has been collected.
