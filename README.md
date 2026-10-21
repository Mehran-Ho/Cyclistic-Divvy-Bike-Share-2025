# Divvy Bike-Share 2025 | Power BI Portfolio Project

**A Power BI analysis of Chicago Divvy bike-share trips in 2025**, inspired by Google's Cyclistic case study. The project compares annual members and casual riders, examines station and route usage, and assesses data quality to inform possible membership-marketing strategies.

## Project objective

How do riding patterns differ between annual members and casual riders? I examine ride frequency, duration, timing, bicycle type, and starting stations and routes. The analysis describes trip patterns; it does not identify individual riders or demonstrate which marketing actions would lead to membership conversions.

## Data and methods

* **Source:** [Divvy trip data](https://divvy-tripdata.s3.amazonaws.com/index.html), 12 monthly CSV files for January–December 2025.
* **Preparation:** Combined files and transformed data in Power Query; calculated ride durations and checked for duplicate records (none found).
* **Analytical filter:** Retained trips with durations greater than 1 minute and less than 120 minutes.
* **Volume:** 5,552,994 original trips; **5,373,769 retained** (96.77%); 179,225 excluded (3.23%).
* **Analysis:** Power Query, DAX queries and measures, and a four-page interactive Power BI report.

## Key findings

|Measure|Result|
|-|-:|
|Total analyzed rides|5,373,769|
|Annual member rides|3,477,474 (64.7%)|
|Casual rides|1,896,295 (35.3%)|
|Average ride duration - members|11.61 minutes|
|Average ride duration - casual riders|17.48 minutes|
|Electric-bike share of rides|64.21%|

* **Trip duration:** Casual rides were longer on average than member rides, for both classic and electric bicycles.
* **Timing:** Member activity was strongest on weekdays, with peaks near 8 AM and 5 PM. Casual activity peaked on Saturdays and tended to rise into the late afternoon.
* **Seasonality:** Both rider groups had substantially more rides in summer.
* **Stations and routes:** Popular casual starting locations included DuSable Lake Shore Dr \& Monroe St and Navy Pier.
* **Data quality:** In the combined source data, 1,093,304 rides lacked a starting station name and 1,123,490 lacked an ending station name, predominantly among electric-bike trips. Station and route rankings therefore cover only rides with recorded station names. A January station-ID investigation also found that some IDs referred to geographically distinct locations, so station names were used for grouping.

## Power BI report

The report contains four pages. Select an image to view the full-size screenshot.

### 1\. 2025 Ridership Overview

![2025 Ridership Overview](screenshots/01\_Ridership\_Overview.png)

### 2\. Rider Behavior

![Rider Behavior](screenshots/02\_Rider\_Behavior.png)

### 3\. Stations \& Routes

![Stations and Routes](screenshots/03\_Stations\_and\_Routes.png)

### 4\. EDA \& Data Quality

![EDA and Data Quality](screenshots/04\_EDA\_and\_Data\_Quality.png)

## Repository contents

* [`screenshots/`](screenshots/) - images of the four Power BI report pages.
* [`dax/selected\_queries.dax`](dax/selected_queries.dax) - six selected DAX queries for rider-type, time-of-day, weekday, month, station, and route analyses.
* [`documentation/methodology\_and\_findings.md`](documentation/methodology_and_findings.md) - detailed data preparation, findings, sensitivity analysis, and limitations.

## Interpretation and limitations

Divvy records **trips, not unique riders**. These data cannot establish an individual's frequency of use, trip purpose, or likelihood of converting to an annual membership. Same-station start/end pairs do not reveal the route actually traveled. Missing station names, particularly for electric-bike rides, affect station and route rankings. The duration filter excludes some potentially valid trips, and one year of data cannot establish long-term trends.

**Potential business application:** The differences in riding patterns can guide further research into targeted membership offers, but the dataset alone cannot establish their effectiveness.


