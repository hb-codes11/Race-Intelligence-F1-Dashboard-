# Formula 1 Race Intelligence Dashboard
## Project development report

**Author:** Harsh Bhadrawale  
**Course:** Data Analytics with Tableau

[Dashboard](https://public.tableau.com/app/profile/harsh.bhadrawale/viz/F1RaceIntelligencedashboard-Harsh/Dashboard1) · [Story](https://public.tableau.com/app/profile/harsh.bhadrawale/viz/F1RaceIntelligencedashboard-Harsh/Story1) · [Website](https://hb-codes11.github.io/Race-Intelligence-F1-Dashboard-/)

## 1. Project background

I developed this project to practise using Tableau with Formula 1 data. I already had some knowledge of the sport, which helped me understand the fields and decide what to compare.

The work started with an Excel workbook and ended with nine Tableau views, a dashboard, a Story, and a website that embeds the published analysis. This report records the steps used to build them and explains how to read the results.

## 2. Problem statement and requirements

The source sheet contains thousands of result records. Comparing drivers, teams, seasons, and race conditions directly in that table would require repeated sorting and calculations.

The problem was to turn those records into charts that answer a small set of questions:

- How do recorded team points change from season to season?
- Which drivers and teams have the highest point totals in the dataset?
- What reasons are recorded for non-finishes?
- How does the share of DNF records vary by weather category?
- How do position measures, starting tyres, and circuit categories compare?

The intended audience is a course reviewer or someone interested in exploring F1 data. The business use case is quicker access to performance and reliability summaries. For actual team strategy or recruitment, the data would need further validation and more context.

The project requirements included data preparation, multiple visualizations, a dashboard, a Story, publication, performance documentation, and a development report. A website was also created to make the published work easier to access.

## 3. Literature review

The supporting references cover two parts of the project: presenting a sequence of charts in Tableau and understanding the racing context.

Tableau's documentation explains how Story points can present views in a sequence. This was useful for organising the nine worksheets into a guided explanation. The Formula 1 beginner guides provide background on championship points and the race weekend.

The project uses the points already recorded in the course workbook. It does not recalculate historical seasons using a single scoring system.

| Reference | Relevance |
|---|---|
| [Tableau: Stories](https://help.tableau.com/current/pro/desktop/en-us/stories.htm) | Organising views into a sequence |
| [Tableau: Create a Story](https://help.tableau.com/current/pro/desktop/en-us/story_create.htm) | Adding sheets and captions to Story points |
| [Formula 1: Drivers' Championship guide](https://www.formula1.com/en/latest/article/the-beginners-guide-to-the-f1-drivers-championship.53MjXJzTDxQnfxfoCLnxNZ) | Background on championship points |
| [Formula 1: Race weekend guide](https://www.formula1.com/en/latest/article/the-beginners-guide-to-the-formula-1-weekend.5RFZzGXNhEi9AEuMXwo987) | Context for race results |

## 4. Social and business relevance

The dashboard gives a viewer one place to compare selected measures instead of working through the spreadsheet. It can be used in a classroom demonstration or as an example of sports data analysis.

The main value of this version is learning and communication. A team analyst could ask similar questions about performance or reliability, but the charts here are summaries of a course dataset. They are not enough on their own to judge a driver's ability or recommend a race strategy.

## 5. Data collection and scope

The dataset was supplied with the course as `F1 Racing Project Dataset.xlsx`. The workbook contains five sheets:

| Sheet | Use in this project |
|---|---|
| `race_results` | Source for the Tableau views |
| `circuits` | Not joined into the current analysis |
| `championship_standings` | Not joined into the current analysis |
| `lap_intelligence` | Not joined into the current analysis |
| `qualifying_results` | Not joined into the current analysis |

Tableau displayed **6,464 rows** for `race_results`. The Season field ranged from **2010 to 2026**. These are properties of the supplied file; they do not confirm that it is a complete or independently verified history of F1.

The Excel file and local Tableau workbook are excluded from this GitHub repository. The published Tableau views are linked at the beginning of this report.

## 6. Data inspection and preparation

### Connecting the file

In Tableau Public, I connected to the Excel workbook and placed `race_results` on the data source canvas. I reviewed the preview and field list before opening the first worksheet.

### Treating Season correctly

One issue appeared in the first chart: Tableau summed the numeric Season field. This produced an axis with very large values instead of individual years. Changing Season to a dimension separated the years and made the team trend readable.

This step mattered because a numeric field is not always a quantity that should be added. Here, Season identifies a group of records.

### Choosing the aggregations

I used the following rules for the worksheets:

| Measure | Aggregation | Reason |
|---|---|---|
| Points | Sum | Compare the total points in each group |
| DNF flag | Sum | Count rows marked as DNF, assuming a 0/1 flag |
| DNF flag by weather | Average | Compare the share of DNF records in each weather group |
| Positions gained | Average | Compare the mean per result record |
| Finish position | Average | Avoid adding finishing ranks together |
| Starting compound | Record count | Count how often each compound appears |

For example, an average DNF flag of 0.06 represents 6% of the records in that weather group, provided the flag is coded as 0 or 1.

DNF records were kept for the reliability views. Blank finish values need to be considered separately when interpreting the average finish chart, since records without a valid finish value do not contribute to that average.

The work did not include a full record-by-record comparison with official race results or a documented duplicate audit. No claim of complete data validation is made.

## 7. Worksheet development

The workbook contains the following nine views. Their titles may use shorter wording in Tableau.

| # | View | Main setup |
|---:|---|---|
| 1 | Team Points by Season | Season on Columns, sum of Points on Rows, Team on Color; line chart |
| 2 | Driver Points Leaderboard | Driver on Rows, sum of Points on Columns; bars sorted by points |
| 3 | DNF by Reason | DNF Reason on Rows, sum of DNF on Columns |
| 4 | DNF by Weather | Weather on Rows, average DNF on Columns |
| 5 | Team Points Leaderboard | Team on Rows, sum of Points on Columns; bars sorted by points |
| 6 | Average Positions Gained by Team | Team grouped by average positions gained |
| 7 | Starting Tyre Distribution | Starting Compound grouped by the count of result records |
| 8 | Race Points by Circuit Type | Circuit Type grouped by sum of Points |
| 9 | Average Finish Position by Team | Team grouped by average finish position |

Season and DNF Reason selections were added in the relevant views. Filter propagation across every dashboard sheet was not fully checked.

## 8. Dashboard and Story

The dashboard combines the worksheet views so the user can move between season trends, rankings, and other comparisons.

The Story uses nine captioned scenes to present the analysis in smaller parts. Each scene focuses on one of the views listed above. This gives a reviewer a way to follow the project without having to interpret every chart at once.

The website provides an embedded Tableau Story and direct access to the published project. The website layout adapts to screen width, but the embedded Tableau content also depends on the workbook's own layout. A full device-by-device review has not been recorded.

## 9. Interpretation and limitations

The driver and team leaderboards make it possible to compare totals within the supplied records. The season chart adds the time dimension, while the DNF charts examine reliability from two different groupings.

These comparisons need to be read carefully:

- A result row represents an entry in the dataset, not a separate Grand Prix. The 6,464 rows must not be described as 6,464 races.
- Driver and team point totals should not be labelled verified career totals.
- Total points by circuit type are affected by how many records belong to each category.
- Starting-compound counts show usage in the recorded data. They do not show which compound is the best strategy.
- Differences in DNF rate by weather do not prove that the weather caused the non-finishes.
- Average finish position depends on the available finish values and should be read alongside DNF information.
- Historical points are used as supplied, without normalising seasons to one scoring system.

Specific rankings and values can change with filters, so they should be read from the published chart together with its selected season range.

## 10. Performance record

| Item | Current record |
|---|---|
| Source rows | 6,464 in `race_results` |
| Worksheet views | 9 |
| Dashboards | 1 |
| Story scenes | 9 |
| Custom calculated fields | None documented for these views; source fields are aggregated in Tableau |
| Filters | Season range and DNF Reason in relevant views |
| Dashboard-wide filter check | Not fully verified |
| Loading-time measurements | Not recorded under controlled conditions |

Publication confirms that the project has been made available online. It does not establish a loading-time benchmark. A repeatable performance test would need a record of the device, network, filter selections, and time taken for each view to load.

## 11. Publishing and web integration

The dashboard and Story were published to Tableau Public under my profile.

The frontend uses HTML, CSS, and a small JavaScript view switcher. It embeds either the dashboard or Story in an iframe and provides direct links to both published views. The website files are stored in GitHub and deployed to GitHub Pages through an Actions workflow.

In the repository settings, GitHub Pages uses **GitHub Actions** as its source. A push to `main` starts the deployment workflow. Tableau serves the embedded visualization; GitHub Pages serves the surrounding website.

## 12. Recreating the project

1. Obtain the course dataset.
2. Open Tableau Public and connect to the Excel workbook.
3. Select `race_results` and review the data preview.
4. Use Season as a dimension for the time-based view.
5. Create the nine worksheets using the groupings and aggregations in Section 7.
6. Add the relevant filters and sort the leaderboards.
7. Assemble the dashboard and create nine Story points with captions.
8. Publish the workbook to your own Tableau Public account.
9. Replace the Tableau URLs in the website and README if recreating the project under a different profile.
10. Deploy the website with GitHub Pages, or open `index.html` locally with an internet connection.

## 13. Submission status

The Tableau dashboard, Story, GitHub documentation, and website have been published. SkillWallet status updates and submission links are handled separately.

The explanation video was deferred. Controlled performance measurements and a complete check of filters and device layouts remain to be recorded.
