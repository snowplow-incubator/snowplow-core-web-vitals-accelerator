+++
title= "Set-up and run core-web-vitals module"
weight = 3
post = ""
+++


#### **Step 1:** Enable the optional core web vitals module
As the [advanced-analytics-for-web accelerator](https://docs.snowplow.io/accelerators/web/) is a prerequisite, it is assumed that you already have a dbt project set-up to process basic web events.

To enable the optional `core web vitals` module, you must add the following code snippet to your dbt_project.yml file:


```yml
models:
  snowplow_web:
    snowplow__enable_cwv: true
```

#### **Step 2:** Change optional parameters

By default, following industry standard practice, the core web vitals are evaluated against the 75 percentile value of all pageviews.

The measurements are executed in a drop and recompute fashion to fit BI purposes and would always show the last 28 days data.

To change either of these default values you can modify the relevant variable in your dbt_project.yml file like so:

```yml
models:
  snowplow_web:
    snowplow__enable_cwv: true
    snowplow__cwv_days_to_measure: 28
    snowplow__cwv_percentile: 75
```

{{%/* notice warning */%}}
Please make sure your `snowplow__backfill_limit_days` variable is not less than the `snowplow__cwv_days_to_measure`. The package will warn you if this happens though.
{{%/* /notice */%}}

#### **Step 3:** Run the package

If this is your first time processing the snowplow_web package then you can run the package the recommended way either through your CLI or from within dbt Cloud with the following command:

```
dbt run --selector snowplow_web
```

If you already have a working snowplow_web package and would like to enable the core web vitals module you do not need to rebuild the whole model from scratch. For the least amount of reprocessing impact execute the first run the following way:

```
dbt run -m snowplow_web.base --vars 'snowplow__start_date: <date_when_core_web_vital_tracking_starts>'
```
This way only the base module is reprocessed. The web model's update logic will recognize the newly enabled models and backfilling should start between the date you defined within snowplow_start_date and the upper limit defined by the variable `snowplow_backfill_limit_days` that is set for the web model.

`Snowplow: New Snowplow incremental model. Backfilling`

You can overwrite this limit for the backfilling process temporarily if needed:

```
# dbt_project.yml

vars:
  snowplow_web:
    snowplow__backfill_limit_days: 1
```

After this you should be able to see all core web vitals models created. Any subsequent run from this point onwards could be carried out using the recommended web model running method - using the snowplow_web selector.

```
dbt run --selector snowplow_web
```

As soon as backfilling finishes, running the model results in both the web and the core web vital models being updated during the same run for the same period, both using the same latest set of data from the `_base_events_this_run` table. Please note that while the backfilling process lasts, no new web events are going to be processed.

The following models will be generated:

- **snowplow_web_vitals**: Incremental table used as a base for storing core web vital events (first event per pageview).

- **snowplow_web_vital_measurements**: Drop and recompute table to use for visualisations that takes core web vital measurements at the user specified percentile point (defaulted to 75).




