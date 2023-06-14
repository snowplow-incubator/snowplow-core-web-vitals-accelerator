+++
title = "Visualize your data"
weight = 1
post = ""
+++


### Introduction

Now that you have modelled data you would probably want to see the results in a visual way as well to be able to easily identify any performance issues with your website. We have created a Tableau workbook to do that, using csvs that were exported from the derived core web vitals tables (`core_web_vitals`, `core_web_vital_measurements`) as the data source. We used the same data source as the sample data provided so all you have to do in this section is to open it up and have a look at the visualizations to get inspiration of what you can build.

### Accessing the sample Tableau workbook

You can download the file from here:

Once you have the file locally, you can open it in serveral ways, opening it in Tableau Public, Tableau Reader (free) or uploading it to Tableau Online if you have access.

### Visualizations

#### Core Web Vitals

Main dashboard with the most important metrics: LCP, FID, CLS and TTFB with most important dimensions such as period, device, top 10 most popular pages and location.

![Core Web Vitals](../images/1.png)

#### Low Performing URLs

Dashboard focusing on the worst performing URLs.

![Low Performing URLs](../images/2.png)

#### Core Web Vitals by Period

Core Web Vital visuals tracked across time.

![LCore Web Vitals by Periods](../images/3.png)

#### Visits

This dashboard focuses on the number of page visits and classifies them according to value and result.

![Visits](../images/4.png)

#### Browser Performance

These visuals show the percentage of good / needs improvement / poor results across web browsers.

![Browser Performance](../images/5.png)

#### Core Web Vitals v2

Another, slightly less dense version of the overview.

![Core Web Vitals v2](../images/6.png)
