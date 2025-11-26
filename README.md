# UK Flight Forecast: Predicting Daily Arrivals at London Airports GB

## Overview
This project analyses and forecasts daily flight arrivals into London using real-world flight data from September 2023. Our goal was to see if we could apply time series forecasting to help with operational planning and airport management.

We used an **ARIMA (AutoRegressive Integrated Moving Average)** model to generate a forecast for flight volumes over a 14-day period.

## The Data
We worked with two primary datasets:
1.  **Flight Data (Sept 2023):** Detailed records of flights, including departure/arrival times and aircraft types.
2.  **Airport Data:** Used to match ICAO codes to actual airport names and countries.

By merging these datasets (matching destination codes), we were able to filter specifically for flights arriving in the UK and aggregate them into daily counts.

## Project Structure
Here is how the repository is organised:

* `Cleaning_&_EDA.ipynb`: The first step. This notebook handles data loading, merging the flight and airport datasets, cleaning up column names, and performing initial Exploratory Data Analysis.
* `ATMProject_ARIMA.ipynb`: The core modelling file. This takes the processed daily arrival data and fits the ARIMA model to generate predictions.
* `london_arrivals_processed.csv`: The cleaned output file used for the time series analysis.
* `Flights_Prediction.pptx`: A presentation summarising our methodology, results, and evaluation.

## Methodology

### 1. Data Cleaning & Preparation
We started by standardising the column names and merging the datasets using a left join on the ICAO codes. This allowed us to identify the destination country for every flight. We then filtered for UK arrivals and grouped the data by date to get a daily count of incoming flights.

### 2. Modelling (ARIMA)
We chose an ARIMA model because it is well-suited for non-stationary data (data where trends change over time). The model was trained on the September historical data to learn the daily rhythm of airport traffic.

### 3. Forecasting
We generated a prediction for the next 14 days. The model successfully captured the general stability of flight schedules, including the noticeable drops in traffic that occur on weekends.

## Key Findings & Results
* **Daily Volume:** Arrivals generally fluctuated between 1,180 and 1,390 flights per day.
* **Weekly Pattern:** There is a clear weekly rhythm, with lower traffic on weekends, which the model picked up on.
* **Accuracy:** While the model slightly over-predicted averages in the first week, it remained within a realistic range and did not show extreme deviations.

## Limitations
The biggest challenge was the scope of the data. We only had access to one month of flight records (September 2023). Because of this, we couldn't analyse long-term seasonal trends, such as holiday peaks or summer rushes.

If we had 6 to 12 months of data, we would likely upgrade to a **SARIMA (Seasonal ARIMA)** model to capture those annual seasonality effects.

## Technologies Used
* **Python**
* **Pandas** (Data manipulation)
* **Statsmodels** (ARIMA modelling)
* **Matplotlib** (Visualisation)

## Team
* Oscar Denche
* Matthew Lester
* Daniel Hernandez
* Milena Musiienko