# Admin boundary data quality reports 

This repository is a placeholder for future work needed to develop data quality reports to compare various admin boundary datasets.

### Background

Our data collection efforts (manual or automated) often leave us with multiple options for the same geographic feature. For example, we may find ourselves with administrative boundary datasets from [OSM](https://www.openstreetmap.org/#map=16/51.7012/-0.9095), [GADM](https://gadm.org/), [CODs](https://data.humdata.org/dashboards/cod), and [geoBoundaries](https://www.geoboundaries.org/). It is time consuming to compare each of these options manually. We need an automated way to assess the quality of various administrative boundary datasets, allowing us to make a well-informed selection about the best available option to use in our humanitarian mapping.

### Desired outcome

A Python module that generates a data quality report for one or more input administrative boundary datasets. This report should summarize the basic attributes and topological characteristics of admin boundary data. This report should be presented in a user-friendly way, allowing a MapAction team member to quickly make a well-informed decision about which data option is best suited for the task at hand. This report should be based on a well-defined definition of the data quality attributes relevant to administrative boundary data.

*Stretch*: Integration of the above Python module with our Pipeline MVP and Jira tasking system, allowing for (semi) automated decision-making.

*Stretch*: Expansion to other data types beyond administrative boundaries, such as road networks and/or health facilities.

### Data quality needs and challenges

It is useful to think about reporting on admin boundary data quality according to established dimensions of geospatial data quality. These are documented in a variety of sources and may vary slightly. Commonly-referenced dimensions include accuracy, completeness, logical consistency, timeliness, and lineage. We commonly ask questions such as: 
- Is this boundary in the right place? (particularly relevant in sensitive political contexts)
- Are there the right number of features in this dataset (eg. is the number of provinces, regions, etc. consistent with the country's official boundaries)?
- Does the geometry of the boundary make sense (eg. we might be hesitant to trust a boundary with a self-intersecting polygon)?
- How recently was this data updated?
- What source does it come from? How much can we trust that source?

When dealing with admin boundary data it is also important to think about the question of scale. For example, are we working with a national boundary or with subnational regional boundaries? This data is commonly referenced according to the naming convention of admin0 (national), admin1 (first subdivision level), admin2 (next subdivision level), etc. 

We must also always think about data quality with respect to a given use case. The way that we want to use a dataset informs the kind of quality needs that we have. For example, if we're creating a national map with admin0 boundary data, we probably don't care that the admin4 level data is incomplete. 

### Getting started 

A good way to begin with this work is to explore how you can answer some of the questions listed above for boundary datasets from OSM, GADM, CODs, and geoBoundaries. You may want to explore how to programmatically report on various elements of each dataset's metadata, quantitative attributes, and geospatial characteristics. Start small with one or two countries to develop a proof of concept and then try to expand from there. 

You may want to focus on countries where we are already engaging in data preparedness work, which include: 
- Bangladesh
- South Sudan
- Myanmar
- Dominican Republic
- Haiti
- Guatemala

Python libraries including [GeoPandas](https://geopandas.org/) and [pandas](https://pandas.pydata.org/) will likely be quite helpful.  