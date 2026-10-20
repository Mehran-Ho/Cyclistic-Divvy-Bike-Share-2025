# Divvy Bike-Share 2025: Methodology and Findings

## 1. Project Objective

Analyze Chicago Divvy bike-share trips during 2025 to compare annual members and casual riders by ride frequency, duration, timing, bicycle type, and station and route usage. The business motivation is to identify behavioral differences that could inform efforts to convert casual riders into annual members.

The project also examines data quality and demonstrates an end-to-end workflow using Power Query, DAX, and interactive Power BI reports. Note that trip records reveal riding patterns, but do not establish individual trip purposes or the effectiveness of particular marketing strategies.

## 2. Data and Methodology

### Source and Power Query Preparation

Twelve monthly CSV files (January–December 2025) from Divvy were combined in Power Query. The combined data was checked for duplicate records; none were found. Ride duration in minutes was calculated from the difference between trip end and start timestamps, assigned a numeric data type, and rounded to two decimal places.

Source: https://divvy-tripdata.s3.amazonaws.com/index.html

### Ride Duration Filtering

A referenced query retained rides satisfying `1 < ride_duration_minutes < 120`. The lower threshold excluded extremely short, zero, or negative durations that may reflect incomplete trips or recording anomalies. The upper threshold limited the influence of unusually long trips on typical-duration statistics; it was an analytical choice, not a Divvy pricing or operational rule.

| Metric | Value |
|---|---|
| Combined records | 5,552,994 |
| Final records after duration filtering | 5,373,769 (96.77%) |
| Records excluded by duration rule | 179,225 (3.23%) |

A sensitivity analysis compared a 120-minute upper threshold with a 180-minute threshold. Average duration increased from approximately 11.61 to 11.71 minutes for members and from 17.48 to 18.32 minutes for casual riders. The conclusion that casual riders take longer trips remained unchanged.

### Station and Geographic Data Quality

Missing station names were concentrated in electric-bike rides: 1,093,304 lacked starting station names and 1,123,433 lacked ending station names. Classic-bike records had no missing starting station names and 57 missing ending station names. Missing names did not necessarily mean missing GPS coordinates; some trips may begin or end at unnamed pickup or drop-off locations.

An investigation of January 2025 data identified eight station IDs associated with two geographically distinct locations, typically a named Divvy station and a location labeled as a Public Rack. Conversely, two named stations - Burling St & Diversey Pkwy and Western Ave & Lake St - each appeared under two different IDs with nearby coordinates. These findings indicated that station IDs were not always reliable identifiers of unique physical locations. Consequently, station names were used for report groupings and route construction.

## 3. Exploratory Analysis and Findings

### Ridership, Duration, and Bicycle Type

| Metric | Value |
|---|---|
| Total rides | 5,373,769 |
| Annual members | 3,477,474 (64.7%) |
| Casual riders | 1,896,295 (35.3%) |
| Average duration - members / casual | 11.61 / 17.48 minutes |
| Overall average duration | 13.68 minutes |
| Electric-bike share | 64.21% |

Casual riders had longer average rides than members. For classic bikes, the averages were 23.02 minutes (casual) and 12.66 minutes (members); for electric bikes, 14.58 and 11.00 minutes, respectively. Electric bikes accounted for approximately 65.7% of casual rides and 63.4% of member rides.

### Seasonal, Weekly, and Hourly Patterns

Both member and casual ridership increased substantially during the summer months. Average ride duration also increased for both groups, with a larger seasonal increase among casual riders. Casual riders consistently had longer average ride durations than members throughout the year.

Saturday had the highest overall daily ride count, while Sunday had the lowest. By rider type, member rides were strongest on weekdays, particularly Tuesday through Thursday, whereas casual rides peaked on Saturday. Member ridership displayed clear peaks near 8 AM and 5 PM; casual activity increased more gradually through the day, peaking in late afternoon. These patterns are consistent with different transportation and leisure uses.

### Starting Stations and Routes

Kingsbury St & Kinzie St was the leading starting station for members, followed by Clinton St & Washington Blvd. For casual riders, DuSable Lake Shore Dr & Monroe St led, followed by Navy Pier. Casual-rider locations were more prominent near the lakefront and visitor attractions.

Leading member routes included connections between Ellis Ave & 60th St and Ellis Ave & 55th St, and other Ellis/University Avenue stations. Leading casual routes included same-named starting and ending stations at DuSable Lake Shore Dr & Monroe St and Navy Pier. Same-station pairs are consistent with recreational use but do not reveal the actual path taken. Rankings cover named stations only and may underrepresent electric-bike activity.

## 4. Power BI Implementation

### Report Design

The project uses a four-page interactive Power BI report: 2025 Ridership Overview, Rider Behavior, Stations & Routes, and EDA & Data Quality. Reports permit multi-page exploration, filtering, and cross-filtering. A Power BI Service dashboard, typically a single-page collection of tiles for metric monitoring, was less suitable for this exploratory comparison.

### Technical Methods

Power Query was used to combine and transform source data and create the filtered analytical dataset. DAX measures and queries supported calculations, exploratory analysis, and verification of selected results. Power BI visuals presented trends, rider-group comparisons, station rankings, and data-quality findings. Selected DAX queries will be included in the GitHub repository as supporting technical documentation.

## 5. Conclusions and Limitations

The analysis revealed distinct riding patterns among annual members and casual riders. Member activity showed patterns consistent with routine transportation, while casual ridership showed patterns consistent with recreational and visitor-oriented travel. These differences were evident in trip timing, duration, and station usage.

These findings suggest opportunities for targeted membership marketing. For example, Divvy could investigate whether casual riders who frequently use the service would benefit from annual membership. Marketing messages could emphasize convenience and potential cost savings for riders whose usage patterns make membership worthwhile.

### Limitations

The dataset records bicycle trips rather than individual rider identities. Consequently, it cannot establish how frequently a particular casual rider uses Divvy or whether that rider would benefit financially from annual membership.

Trip timing, duration, and location provide indirect indications of possible trip purposes, but they cannot establish whether an individual trip was for commuting, recreation, or another activity.

The exclusion of rides lasting one minute or less or 120 minutes or more was an analytical decision intended to improve comparability. Some excluded rides may have been legitimate.

Missing station names, particularly for electric-bike rides, limit the completeness of station and route analyses. Consequently, the reported rankings reflect only rides with station names and may not fully represent actual usage patterns.

Finally, the analysis covers only 2025. Seasonal patterns are observable within that year, but longer-term trends and year-to-year changes cannot be established without additional data.
