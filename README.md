# Global Climate Change Tracking & Forecasting: EDA and ML Projections for 2100

## Project Team
* **İrem Akyol** - 24061617 (Project Lead)
* **Murat Bilgin** - 23061701

## Project Overview
This project advances global climate monitoring by leveraging Exploratory Data Analysis (EDA) of historical temperature records to directly support **Sustainable Development Goal (SDG) 13: Climate Action**. By establishing a definitive climate baseline, the analysis highlights the critical historical shift in global land temperatures from a ~8.0°C baseline to over 9.5°C. 

Going beyond descriptive statistics, this project utilizes advanced Machine Learning architectures to forecast climate trajectories up to the year 2100. A core conclusion of our research dispels the "Sinking Nations" misconception; the true imminent threat by 2100 is systemic infrastructure failure, chronic inland flooding, and coastal erosion destroying habitability long before landmasses are permanently submerged.

## Datasets Used
* **Berkeley Earth Climate Data**: A multi-layered spatiotemporal dataset including `GlobalTemperatures.csv`, `GlobalLandTemperaturesByCountry.csv`, and granular city/state-level records.
* **Global Sea Level Rise Data**: Historical observations measuring global mean sea level anomalies.

## Methodology & Workflow
1. **Data Cleaning & Preprocessing**: Identified and resolved missing values (NaNs) from pre-19th-century records using targeted `.dropna()` methods to prevent historical bias. Extracted datetime objects for chronological indexing.
2. **Data Aggregation**: Grouped spatiotemporal data by year to compute annual mean temperatures, successfully filtering out short-term localized "noise" and temporary extreme anomalies (e.g., volcanic events).
3. **Predictive Modeling (2100 Forecasts)**: Benchmarked various learning paradigms using Root Mean Square Error (RMSE) to capture non-linear trends and long-term dynamics:
   * Polynomial Regression (Degrees 2 to 5)
   * XGBoost
   * Random Forest
   * Long Short-Term Memory (LSTM) Networks

## Key Findings & Model Performance
Extensive hyperparameter optimization (testing splits of 0.05, 0.10, and 0.20) yielded the following optimal configurations:

* **Global Land Temperature Forecast**: The most accurate long-term projection was achieved using **5th-degree Polynomial Regression** (Test Size: 0.05), resulting in a minimum **RMSE of 0.1495°C**. While LSTM achieved a low RMSE of 0.2378°C, deeper analysis revealed a "lag-phase trap" (naive forecasting bias), making it less reliable for generalizing overarching non-linear climate acceleration.
* **Sea Level Rise Forecast**: The **XGBoost** algorithm (Test Size: 0.05) delivered the highest predictive precision with an **RMSE of 4.2106 mm**.
* **Impact Multiplier**: The projected anomalies dictate that even a few centimeters of deviation in sea level will trigger a domino effect, leading to municipal sewage backup, freshwater contamination, and global supply chain disruptions.

## Repository Structure
* `/data`: Contains the raw and aggregated CSV files used for training and testing.
* `/notebooks`: Jupyter Notebooks detailing the EDA, data cleaning, model training, and time-series visualizations.
* `/docs`: Detailed project reports and concept notes discussing the systemic risks of climate change.

## How to Run
1. Clone the repository.
2. Install the required dependencies:
   ```bash
   pip install pandas matplotlib seaborn scikit-learn xgboost kagglehub
