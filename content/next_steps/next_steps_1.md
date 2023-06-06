+++
title = "Model your pipeline data"
weight = 1
post = ""
+++

At this stage you should:

- Have tracking and enrichment set-up
- Have this data in the `ATOMIC.EVENTS` table
- Have a working dbt project with the snowplow-web model's core web vital module configurations for the sample data

#### **Step 1:** Complete refresh of your Snowplow web package (Optional)

If you would like to use your current dbt environment that you set-up during modeling the sample data you might want to start from scratch.

While you can drop and recompute the incremental tables within this package using the standard `--full-refresh` flag, all manifest tables are protected from being dropped in production. Without dropping the manifest during a full refresh, the selected derived incremental tables would be dropped but the processing of events would resume from where the package left off (as captured by the `snowplow_web_incremental_manifest` table) rather than your `snowplow__start_date`.

In order to drop all the manifest tables and start again set the `snowplow__allow_refresh` variable to `true` at run time:

```bash
dbt run --select snowplow_web tag:snowplow_web_incremental --full-refresh --vars 'snowplow__allow_refresh: true'
# or using selector flag
dbt run --selector snowplow_web --full-refresh --vars 'snowplow__allow_refresh: true'
```

#### **Step 2:** Modify variables

Assuming that you followed the guide on how to run the data model on the sample data, here we will only highlight the differences in the set-up:

- Remove the `snowplow__events` variable. This time the base table will be the default `atomic.events`, therefore no need to overwrite it.

- Change the `snowplow__start_date` variable according to the data you have in your events table.

#### **Step 3:** Run the snowplow_web model

Execute the following either through your CLI or from within dbt Cloud

```
dbt run --selector snowplow_web
```

Depending on the period of data available since the `snowplow__start_date` and the `snowplow__backfill_limit_days` variable you might not process all your data during your first run. Each time the model runs it should display the period it processes and the timestamp of the last event processed for each model within the package. This gets saved in the `snowplow__incremental_manifest` table so you can always check the data processing state (see below).

![manifest](../images/manifest.png)

#### **Step 4:** Run dbt test

Run our recommended selector specified tests to identify potential issues with the data:

```bash
dbt test --selector snowplow_web_lean_tests
```
***

*Congratulations! You've finished the Web Performance accelerator.*
