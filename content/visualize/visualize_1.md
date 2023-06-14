+++
title = "Visualize your data"
weight = 1
post = ""
+++

#### Introduction

Now that you have modelled data you would probably want to see the results in a visual way as well to be able to easily identify any performance issues with your website.

We have created a Tableau workbook to snowcase how you could do that, using csvs that were exported from the derived core web vitals tables (`core_web_vitals`, `core_web_vital_measurements`) with [this sample csv](add link to S3) as the data source.

If you would like to see your own modelled data you can simply change the data sources and then you will be able to look at the visualizations to get inspiration of what you can build with your connector of choice (based on the warehouse you have).

#### Accessing the sample Tableau workbook

You can download the file from here:

Once you have the file locally, you can open it in serveral ways: with Tableau Public, Tableau Reader (free) or by uploading it to Tableau Online, if you have access.

#### Change the dashboard data source

1. Export the `derived.snowplow_web_vitals` and `snowplow_web_vital_measurements` as csv with your sql editor of choice.

2. In Tableau Public or Tableu Online open the sample twbx file and unhide one of the worksheets (E.g. Go to Core Web Vitals dashboard and select LCP by period and device then right click and uncheck the `Hide` box)

3. Go to `Data/ New Data Source` select `text file` and navigate to the downloaded `snowplow_web_vital_measurements.csv`. Go back to the unhidden worksheet. Now you can see the new data source added at the top left corner.

4. Select it and make the following changes:

 - change the `Time Period` to `Date and Time` by clicking on the `Abc` icon in front of its name
 - create set by right-clicking on `Device Class` then choose `Create / Set`, tick `all` and tick the box `exclude` to exlude results with `all` in the name, click ok

5. Go to `Data / Replace data source` and select the new `snowplow_web_vital_measurements` file to replace `snowplow_web_vital_measurements_sample` in the `Replacement` section.

6. You can right click and `Close` the original `snowplow_web_vital_measurements_sample` data connection from the upper `Data` section of the page.

7. Add and replace the `snowplow_web_vitals_sample` as well. For that you do not need any changes to the fields. (Step 3, 5, 6 are needed again)

You should have a working dashboard with your own data! Feel free to pick and choose visualizations and dashboards to make your custom one.

![Chrome Extension](../images/1.png?width=50pc)
