+++
title = "Introduction"
menuTitle = "Introduction"
pre = "<i class='fas fa-rocket'></i> "
chapter = false
weight = 1
+++

### Web Performance Accelerator

#### Introduction

This accelerator will show you how to track and model raw `core web vital` events so that you can monitor your website's performance via the most essential metrics. Improving the web performance can have a dramatic impact on how your users view and interact with your website with the potential to maximise your revenue.

!['Potential impact'](images/impact.png?height=20pc)

Here you will learn to:

- Model and Visualise Snowplow data
    - using the [snowplow_web](https://hub.getdbt.com/snowplow/snowplow_web/latest/) dbt package
    - using our sample data (no need to have a working pipeline)
- Set-up Snowplow Tracking and Enrichment to prepare your data sources
- Apply what you have learned on your own pipeline to gain insights
***

#### Who is this guide for?

Data practitioners who would like to:
- Easily capture [core web vitals](https://web.dev/vitals/) on their website using the Javascript tracker
- Report and visualise the proportion of vitals [within target](https://web.dev/vitals/#core-web-vitals) using **Tableau**

***

#### What you will learn

In an estimated minimum of a day (~6.5 hours) you can achieve the following:

- **Upload -** Upload some sample data
- **Model -** Configure and run the `core-web-vital` module of the `snowplow-web` data model
- **Visualize -** Learn how to to set up the Tableau twbx template
- **Track -** Set-up and deploy tracking needed for your website performance data
- **Enrich -** Add an enrichment to your data
- **Next steps -** Gain value from your own pipeline data


{{<mermaid>}}
gantt
dateFormat HH-mm
axisFormat %H:%M
section 1. Upload
30min :upload, 00-00, 30m
section 2. Model
1h :model, after upload, 1h
section 3. Visualise
2h :visualise, after model, 2h
section 4. Track
1h :track, after visualise, 1h
section 5. Enrich
1h :enrich, after track, 1h
section 6. Next steps
1h :next steps, after enrich, 1h

{{</mermaid >}}

{{% notice info %}}
You don't necessarily need to follow all the steps in order. You could choose to skip steps 1-3 where you would learn how to model Website Performance through the sample data. If you have your own website or single page application, you could follow steps 4-6 to run the analysis on your own data right away and go through the modeling steps afterwards.
{{% /notice %}}
***

#### Prerequisites

- It is assumed that you are already familiar with the [snowplow-web](https://hub.getdbt.com/snowplow/snowplow_web/latest/) dbt package. If not, we recommend completing the [Advanced Analytics for Web](https://docs.snowplow.io/accelerators/web) accelerator.

**Modeling**
- dbt CLI installed / dbt Cloud account available
- New dbt project created and configured
- Python 3 Installed
- Snowflake, Databricks or BigQuery account and a user with access to create schemas and tables

**Tracking and Enrichment**
- Snowplow pipeline
- Web app to implement tracking

