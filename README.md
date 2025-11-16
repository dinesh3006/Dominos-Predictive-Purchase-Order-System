# 🍕 Dominos - Predictive Purchase Order System

## Project Overview

This project implements a predictive system to accurately forecast pizza sales and dynamically generate necessary ingredient purchase orders. The primary goal is to **optimize inventory management** by ensuring adequate stock of ingredients to meet upcoming customer demand, minimizing waste and preventing stockouts.

## Key Objectives

1.  **Sales Forecasting**: Predict pizza sales quantity for the next week and for longer periods (e.g., 3 months) using time-series modeling.
2.  **Ingredient Planning**: Calculate the required quantity of every ingredient based on the forecasted sales to ensure sufficient inventory for production.

## Methodology

The core of this system uses a time-series forecasting approach on historical sales data.

### 1. Data Understanding & Exploration (EDA)

The system works with two datasets: **Pizza Sales Data** (48,620 records) and **Pizza Ingredients Data** (518 records).

* **Data Quality Check**: The initial EDA identified minimal missing values (all less than 1%) in the Sales data, specifically for:
    * `pizza_category` (0.05% missing)
    * `pizza_name_id`, `pizza_ingredients`, `pizza_name` (approx. 0.03% missing)
    * `total_price` (0.01% missing)
* **No duplicate rows** were found in either dataset.

### 2. Time Series Forecasting (SARIMA)

The sales data was aggregated and modeled using the **SARIMAX** (Seasonal AutoRegressive Integrated Moving Average with Exogenous Regressors) model to capture both trend and seasonal patterns in the pizza sales time series.

## Results

### Sales Forecast Summary

The predictive model generated forecasts for individual pizza types to plan future capacity:

| Forecast Period   | Total Predicted Pizza Sales |
| :---              | :---                        |
| **Next Week**     | **3,387 pizzas**            |
| **Next 3 Months** | **69,234 pizzas**           |

### Ingredient Purchase Order

Based on the next week's forecast, the system calculates the necessary ingredient quantities (in grams) for resupply:

| Ingredient     | Predicted Quantity (grams) |
| :---           | :---                       |
| **Chicken**    | **75,150.00**              |
| **Red Onions** | **66,980.00**              |
| **Tomatoes**   | **45,490.00**              |
| **Bacon**      | **24,930.00**              |
| **Mushrooms**  | **23,380.00**              |
| **Pepperoni**  | **23,060.00**              |

*This calculation includes the breakdown of ingredients for all pizza types and their predicted sales volume.*

***

## Technologies Used

* **Python**
* **Pandas**: For data manipulation and cleaning.
* **Statsmodels (SARIMAX)**: For time series forecasting.
* **Jupyter/Colab**: For development and execution environment.
