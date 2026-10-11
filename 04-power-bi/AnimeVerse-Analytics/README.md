# AnimeVerse Analytics — Power BI Project

## Overview
AnimeVerse Analytics is an interactive Power BI project for exploring anime data across genres, studios, formats, audience engagement, ratings, and release dates.

## Tools
- Microsoft Power BI Desktop
- Power Query
- DAX
- CSV dataset

## Progress — October 11, 2026

### Completed
- Imported the anime CSV dataset into Power BI.
- Promoted and verified column headers.
- Reviewed data quality across the dataset.
- Removed the unused `image` column while retaining `titleJa`.
- Replaced missing studio values with `Unknown`.
- Preserved missing scores, ranks, end dates, and other meaningful missing values.
- Created `display_title` using `titleEn` when available and falling back to `title`.
- Verified that `id` contains 25,644 distinct, unique values.
- Loaded the cleaned data into Power BI.
- Created the `Total Anime` DAX measure.

### In progress
- Create additional DAX measures.
- Build KPI cards and analytical visuals.
- Develop genre, studio, ranking, and audience-engagement analysis.

## Planned Dashboard
- Total anime
- Average anime score
- Total studios
- Anime distribution by media type and status
- Genre analysis
- Top-ranked anime
- Studio insights
- Release-date trends

## Learning Goals
Practise data cleaning, data profiling, DAX measures, interactive visualizations, and dashboard design.

## Note
The dashboard and remaining measures are still in progress.
