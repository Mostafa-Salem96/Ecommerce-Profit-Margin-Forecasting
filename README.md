# E-commerce Profit Margin Forecasting

This repository contains the implementation of my master thesis project on **financial profit margin forecasting in the e-commerce sector** using a hybrid **SARIMAX–XGBoost** forecasting approach.

The project focuses on predicting profit margin from anonymized e-commerce transaction data by combining statistical time-series modelling with machine learning. SARIMAX is used to capture linear temporal dependencies and weekly seasonality, while XGBoost is applied to SARIMAX residuals to model nonlinear patterns and improve forecasting accuracy.

---

## Thesis Title

**Hybrid SARIMAX–XGBoost Forecasting for E-commerce Profit Margin Prediction**

---

## Project Overview

The expansion of e-commerce has increased competition among digital businesses. In this environment, accurate forecasting is important for pricing, inventory planning, budgeting, resource allocation, and financial decision-making.

Profit margin is a key financial indicator because it shows the relationship between revenue and operating costs. However, forecasting profit margin is more complex than forecasting sales alone because profit margin is affected by several factors, including:

- Customer demand variation
- Seasonality
- Pricing changes
- Freight and delivery costs
- Product cost variation
- Product-category differences
- Calendar and holiday effects

This project proposes a hybrid forecasting framework that combines the strengths of SARIMAX and XGBoost. The goal is to improve forecasting accuracy compared with using a standalone statistical model.

---

## Research Problem

Accurate financial profit margin forecasting is important for e-commerce businesses because it supports strategic planning and operational decisions. However, profit margin forecasting is challenging because the target variable is influenced by both revenue-side and cost-side factors.

Traditional statistical forecasting models such as SARIMAX are effective for capturing temporal dependence, seasonality, and linear time-series patterns. However, they may not fully capture nonlinear relationships caused by customer behavior, pricing variation, freight cost changes, and product-category heterogeneity.

Machine learning models such as XGBoost can capture nonlinear relationships, but they may not fully represent seasonal time-series structures when used alone.

Therefore, this thesis applies a hybrid approach where:

1. SARIMAX captures the linear and seasonal structure of the profit margin time series.
2. XGBoost learns the remaining nonlinear residual patterns.
3. The final forecast combines both model outputs.

---

## Research Aim

The aim of this study is to develop and evaluate a hybrid time-series forecasting approach for predicting financial profit margins in the e-commerce sector by combining SARIMAX and XGBoost.

The research investigates whether applying XGBoost to SARIMAX residuals can improve forecasting accuracy compared with using SARIMAX alone.

---

## Research Objectives

The main objectives of the project are:

- To integrate and prepare an anonymized e-commerce transactional dataset
- To calculate revenue, total cost, profit, and profit margin
- To analyze temporal and seasonal patterns in daily profit margin behavior
- To engineer forecasting features such as lag variables, rolling statistics, temporal variables, and holiday indicators
- To develop a SARIMAX model for capturing linear temporal dependencies and weekly seasonality
- To apply XGBoost to SARIMAX residuals for nonlinear residual learning
- To develop a hybrid SARIMAX–XGBoost forecasting framework
- To evaluate model performance using MAE and RMSE
- To compare forecasting results between SARIMAX and the hybrid model
- To analyze model performance across different product categories

---

## Research Questions

This project addresses the following research questions:

**RQ1:** How effectively can SARIMAX capture temporal dependencies and seasonal patterns in financial profit margin data in the e-commerce sector?

**RQ2:** To what extent can XGBoost improve profit margin forecasting accuracy when applied to SARIMAX residuals compared with using SARIMAX alone?

**RQ3:** How does predictive model performance vary across different product categories?

---

## Dataset Description

The project uses an anonymized transactional retail dataset covering the period from **2023 to 2025**.

The dataset includes multiple relational tables representing different areas of e-commerce activity, including:

- Customers
- Merchants
- Products
- Purchases
- Purchase lines
- Payments
- Reviews

After filtering, cleaning, and integration, the final analytical dataset contains more than **108,000 transaction records**. These records are used to construct the daily profit margin time series and support category-level forecasting analysis.

---

## Dataset Tables

The dataset contains the following relational tables:

- `dim_customers.xls` — customer information
- `dim_merchants.xls` — merchant or seller information
- `dim_products.xls` — product and category information
- `dim_purchaselines.xls` — item-level purchase details
- `fact_purchases.xls` — order-level transaction records
- `fact_purchase_payments.xls` — payment-related information
- `fact_purchase_reviews.xls` — customer review information

These tables are integrated to create a unified analytical dataset for profit margin forecasting.

---

## Target Variable

The main target variable in this project is **profit margin**.

Profit margin is selected because it combines revenue and cost information into one financial performance measure.

The main financial variables used are:

- **Revenue**: represented by the selling price
- **Total cost**: calculated using product cost and delivery or freight cost
- **Profit**: calculated as revenue minus total cost
- **Profit margin**: calculated from profit and revenue

Profit margin is important because it reflects how efficiently revenue is converted into profit after considering operating costs.

---

## Methodology

The methodology follows a sequential hybrid forecasting framework.

The main stages are:

1. Data loading
2. Data inspection
3. Data cleaning and preprocessing
4. Integration of relational tables
5. Profit margin calculation
6. Exploratory data analysis
7. Feature engineering
8. SARIMAX model development
9. XGBoost residual learning
10. Hybrid SARIMAX–XGBoost forecasting
11. Model evaluation
12. Category-level performance analysis

---

## Data Preprocessing

The preprocessing stage prepares the raw relational tables for forecasting analysis.

The main preprocessing steps include:

- Checking missing values
- Removing duplicates
- Converting date columns into datetime format
- Validating numeric columns
- Filtering completed or delivered purchases
- Integrating relational tables
- Creating a final transaction-level analytical dataset
- Aggregating data into a daily profit margin time series

This step is important because forecasting performance depends strongly on the quality and consistency of the prepared dataset.

---

## Exploratory Data Analysis

Exploratory data analysis is used to understand the behavior of the profit margin series before model development.

The analysis focuses on:

- Daily profit margin movement over time
- Temporal patterns
- Weekly seasonality
- Profit margin stability
- Outliers and irregular observations
- Product-category variation
- Holiday-related behavior

The analysis shows that the daily profit margin series contains temporal structure, weekly seasonal behavior, and category-level differences. These findings support the use of a time-series forecasting model and a hybrid modelling approach.

---

## Feature Engineering

Feature engineering is applied to create explanatory variables for forecasting.

The main feature groups include:

### Temporal Features

Temporal features are derived from the date structure and help capture calendar patterns.

Examples include:

- Day of week
- Month
- Date-related variables

### Lag Variables

Lag variables represent previous profit margin values. They help the model understand short-term temporal dependence.

Examples include:

- Previous day profit margin
- Previous week profit margin
- Residual lag values for hybrid modelling

### Rolling Statistics

Rolling statistics summarize recent historical behavior.

Examples include:

- Rolling mean
- Rolling standard deviation
- Rolling minimum
- Rolling maximum

### Holiday Indicators

Holiday-related variables are included because customer demand, logistics, and purchasing behavior may change around public holidays or special calendar events.

---

## Forecasting Models

This project uses three main forecasting components:

1. SARIMAX
2. XGBoost
3. Hybrid SARIMAX–XGBoost

---

## SARIMAX Model

SARIMAX is used as the benchmark statistical model.

It is suitable for this project because it can capture:

- Autoregressive behavior
- Moving-average error structure
- Differencing
- Weekly seasonality
- Linear temporal dependencies
- Exogenous calendar effects

The final SARIMAX specification used in the thesis is:
SARIMAX (2,1,1) (1,0,1,7)
