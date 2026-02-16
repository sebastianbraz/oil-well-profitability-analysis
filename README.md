# Oil Well Profitability and Risk Analysis (OilyGiant)

## Overview
This project evaluates three oil-producing regions to determine the most economically viable location for developing 200 new oil wells. The objective is to maximize expected profit while minimizing financial risk.

A machine learning model was used to predict reserve volumes, followed by profit estimation and uncertainty analysis using bootstrapping.

## Business Objective
Given:
- Revenue per unit (1,000 barrels): $4,500
- Budget: $100 million for 200 wells

The goal is to identify the region that provides:
1. The highest expected profit
2. Acceptable risk of loss

## Methodology

### 1. Model Training and Validation
- Data was split into training and validation sets (75:25).
- A Linear Regression model was trained separately for each region.
- Model performance was evaluated using RMSE.
- Predictions were used to select the top 200 wells per region.

### 2. Baseline Analysis
A baseline scenario was computed using the regional mean reserve volume to simulate random well selection. This demonstrated that average wells would not reach the break-even threshold.

### 3. Profit Calculation
For each region:
- The 200 wells with the highest predicted reserves were selected.
- Actual reserve volumes from the validation set were summed.
- Revenue and profit were calculated.

### 4. Risk Assessment (Bootstrapping)
- 1000 bootstrap samples were generated.
- Profit distribution was estimated.
- Average profit, 95% confidence interval, and probability of loss were calculated.

## Results

| Region | Avg Profit ($) | 95% CI | Risk of Loss |
|--------|----------------|--------|--------------|
| Geo 0  | 3.82M | -0.53M to 7.86M | 7.30% |
| Geo 1  | 4.52M | 1.10M to 7.84M | 0.70% |
| Geo 2  | 3.90M | -0.66M to 8.59M | 7.70% |

## Final Recommendation
Although Geo 0 initially showed strong point-estimate profit, uncertainty analysis revealed that Geo 1 provides:

- The highest average profit
- A fully positive 95% confidence interval
- The lowest probability of loss (0.70%)

Considering both return and risk, **Geo 1 is the most economically justified region for investment.**

## Dataset

The dataset is not included in this repository.

To run the notebook:
1. Create a folder named `data/`
2. Place the required CSV files (`geo_0.csv`, `geo_1.csv`, `geo_2.csv`) inside that folder
3. Run the notebook from top to bottom

## How to Run
1. Place the datasets (`geo_0.csv`, `geo_1.csv`, `geo_2.csv`) inside a `data/` folder.
2. Run the notebook from top to bottom.

Required libraries:
- pandas
- numpy
- scikit-learn

