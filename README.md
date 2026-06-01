# A/B Testing Statistical Significance Tool

![Python](https://img.shields.io/badge/Python-3.x-blue)
![SQL](https://img.shields.io/badge/SQL-BigQuery-blueviolet)
![Tableau](https://img.shields.io/badge/Tableau-Dashboard-orange)
![Statistics](https://img.shields.io/badge/Statistics-Z--test-green)

## Overview

This project is an A/B testing analysis tool built with **BigQuery SQL**, **Python**, and **Tableau**.

The goal is to evaluate whether the differences between control and test groups are statistically significant for key funnel metrics. The analysis is performed both at the overall test level and across separate user segments.

The project includes:

* data extraction and aggregation in BigQuery;
* statistical significance calculations in Python;
* a dynamic Tableau dashboard;
* segment-level analysis by channel, continent, country, and device.

## Dashboard Preview

![A/B Testing Dashboard](https://github.com/fl1rry/ab-test-with-significance/blob/1144844384d9da2199023f245ee09c12ee5e8f1a/A_B%20Test.png)

[Full Tableau Dashboard](https://public.tableau.com/app/profile/oleksandra.yakovenko/viz/ABTestingToolwithSignificance/Dashboard3)

## Metrics

The analysis covers four conversion metrics:

* `add_payment_info / session`
* `add_shipping_info / session`
* `begin_checkout / session`
* `new_account / session`

Each metric is calculated as the number of sessions with the target event divided by the total number of sessions.

## Methodology

The project compares two independent groups:

* **Group A** — control group
* **Group B** — test group

For each metric, the analysis calculates:

* conversion rate for the control group;
* conversion rate for the test group;
* relative metric change;
* z-statistic;
* p-value;
* statistical significance flag.

A **two-proportion z-test** is used because the analyzed metrics are conversion rates.

The significance threshold is:

```text
alpha = 0.05
```

A result is considered statistically significant when:

```text
p-value < 0.05
```

For segment-level analysis, the notebook also applies the **Benjamini–Hochberg FDR correction** to reduce the risk of false-positive conclusions when multiple hypotheses are tested.

## Data Preparation

The SQL query aggregates data from BigQuery into a long-format dataset with the following dimensions:

* date;
* test number;
* test group;
* country;
* continent;
* device;
* acquisition channel;
* event name;
* event count.

The Python notebook transforms the aggregated data into Tableau-ready CSV files.

## Tableau Dashboard

The dashboard contains two analytical sections.

### Total Significance

Shows the overall result for each metric within the selected A/B test.

The table includes:

* conversion rate for Group A;
* conversion rate for Group B;
* relative metric change;
* p-value;
* z-statistic.

### Segments Significance

Allows users to explore results for a selected segment.

Available levels of detail:

* channel;
* continent;
* country;
* device.

Available dashboard filters:

* `Test`
* `Level Of Details`
* `Segment`

## Output Files

The notebook generates Tableau-ready CSV files, which were later used to produce an interactive Tableau Dashboard.

## Tools and Skills

* BigQuery SQL
* Python
* pandas
* statsmodels
* A/B testing
* statistical hypothesis testing
* two-proportion z-test
* multiple testing correction
* Tableau
* dashboard design
* data visualization

## Author

**Oleksandra Yakovenko**
