# E-Commerce-Conversion-Pipeline-R-SQL
End-to-end data engineering pipeline and statistical modeling to analyze e-commerce conversion drivers using SQL and R (MICE, Logistic Regression).


# 🛒 E-Commerce Data Engineering & Conversion Modeling

*Disclaimer: This repository contains data engineering pipelines and statistical models developed for an academic assignment in collaboration with a leading e-commerce retailer. To comply with Non-Disclosure Agreements (NDA), all proprietary data, specific database schemas, exact business metrics, and brand names have been completely anonymized or omitted. The code is provided solely to demonstrate technical methodologies and data architecture.*

## 📊 Project Overview
This project builds an end-to-end data pipeline to analyze session-based conversion rates in a highly seasonal e-commerce category. By integrating internal transactional logs with external APIs (weather data and search trends), the project aims to quantify the impact of user behavior, device usage, and contextual factors on purchasing probability.

## 🛠️ Data Engineering Pipeline (SQL)
The data preparation phase was handled using **PostgreSQL** to aggregate raw event logs into a clean, session-level analytical dataset:
* **Feature Engineering**: Extracted temporal variables (weekends, time of day) and browsing metrics (number of distinct product categories viewed).
* **Window Functions**: Calculated dynamic brand familiarity scores (`session_brand_weight`) by partitioning historical purchase data using `DATE_TRUNC` and `OVER()`.
* **Data Integration**: Joined multiple relational tables (`article_events`, `article`, `customers`) to create a flattened, enriched session table (`sessions_enriched`).

## 📈 Statistical Modeling & Data Science (R)
The analytical dataset was processed and modeled in **R**, addressing real-world data imperfections:
* **Missing Data Imputation**: Handled missing demographic and device data using **Multiple Imputation by Chained Equations (MICE)**, applying Predictive Mean Matching (PMM) and Polytomous Regression.
* **Outlier Detection**: Identified multivariate outliers using the **Mahalanobis Distance** against a Chi-square distribution cutoff.
* **Hypothesis Testing**: Conducted Pearson's Chi-square tests for categorical associations.
* **Multivariable Logistic Regression**: Estimated the probability of conversion controlling for multicollinearity (assessed via Adjusted VIF).
* **Data Visualization**: Built custom probability plots with 95% confidence intervals using `ggplot2` to visualize log-odds predictions.

## 💡 Key Methodological Insights
While business results are confidential, the methodological framework successfully demonstrated that:
1. **Behavioral features** (e.g., browsing variety, brand familiarity) generally provide stronger predictive power for conversion than static demographic traits.
2. **Channel constraints** (mobile vs. desktop friction) can be mathematically quantified to prioritize UX optimizations.
3. **Contextual API data** (sunlight duration, temperature) serve as effective secondary covariates to refine the model's accuracy in seasonal categories.

## 💻 Tech Stack
* **Database / ETL**: SQL (PostgreSQL)
* **Language**: R
* **Key Libraries**: `tidyverse`, `mice` (Data Imputation), `lubridate`, `car` (VIF analysis), `broom`, `scales`
