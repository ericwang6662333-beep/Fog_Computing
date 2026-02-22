# Fog Computing-Based Smart Energy Management System

## Overview
This repository contains the implementation of a residential smart energy management system utilizing Fog Computing and Machine Learning. The project aims to optimize the energy scheduling of a home battery storage system (prosumer) in a dynamic Time-of-Use (ToU) pricing environment. 

A key focus of this research is the integration of realistic market constraints, specifically an asymmetric pricing model where the Feed-in Tariff (FiT) is capped at 20% of the retail electricity price, grounded in real-world energy policies (e.g., UK Ofgem guidelines).

## Key Features
* **Machine Learning Forecasting**: Utilizes a Random Forest regressor to predict future energy generation and consumption based on historical environmental and usage data.
* **Fog Node Edge Computing**: Simulates localized, low-latency decision-making for battery charging and discharging.
* **Time-of-Use (ToU) Optimization**: Implements an intelligent algorithm that purchases heavily discounted electricity during off-peak night hours and discharges during daytime peak hours to offset expensive grid demand.
* **Asymmetric Pricing Simulation**: Accurately models the financial penalty of exporting energy to the grid versus self-consumption, forcing the algorithm to prioritize self-sufficiency over simple arbitrage.
* **Continuous Financial Evaluation**: Includes an automated simulation loop to compare the Fog Computing strategy against a baseline (no battery) scenario over a continuous period.

## Repository Structure
* `2.ipynb`: The main Jupyter Notebook containing the end-to-end pipeline.
* `HomeC.csv`: The primary historical dataset containing hourly energy load, solar generation, and pricing data.
* *(Note: Due to GitHub file size limits, this file is not included in the repository. Please download it and place it in the root directory before running the code.)*
* `.gitignore`: Configured to ignore large datasets like `*.csv` to prevent upload errors.

## Dependencies
The code is written in Python 3.x. The primary libraries required to run the notebook are:
* pandas
* scikit-learn
* matplotlib
* numpy

You can install the dependencies using pip:
`pip install pandas scikit-learn matplotlib numpy`

## Usage
1. Clone this repository to your local machine.
2. Ensure the dataset file `HomeC.csv` is placed in the root directory of the cloned repository.
3. Open `2.ipynb` using Jupyter Notebook or VS Code.
4. Run the cells sequentially. The final cell will output a cumulative cost comparison graph and calculate the Total Money Saved and Savings Percentage.

## Methodology Highlights
The algorithm transitions from a purely aggressive arbitrage strategy to a hybrid **Smart Peak Shaving / ToU** strategy. Early simulations proved that indiscriminate exporting to the grid results in financial loss due to the low FiT rate. The current model successfully navigates this by:
1.  Charging the battery with 100% free excess solar energy when available.
2.  Charging from the grid only when the price drops below a specific threshold (e.g., off-peak winter nights).
3.  Discharging strictly to offset home load during peak pricing events.

## Results
Operating under strict real-world market constraints, the Fog Node intelligent strategy successfully flattens the cumulative cost curve compared to a traditional baseline setup, achieving significant and stable cost reductions even during winter months with low solar irradiance.
