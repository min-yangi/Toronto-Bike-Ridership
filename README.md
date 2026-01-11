# Bike Share Toronto Ridership Growth Optimization
Humber Polytechnic | BIA 5450 Capstone Project | Group 3 (InsightOps)

## 🚴 Project Summary
This capstone project provides a comprehensive analysis of Bike Share Toronto (BST) to improve service efficiency, user accessibility, and membership conversion. Despite reaching a record 4.6 million trips in 2023, the system faces challenges such as low membership rates (10%), winter ridership declines, and station imbalances in underserved areas like Etobicoke and North York.


## 🛠️ The "InsightOps" Solution
We developed a multi-faceted analytical framework consisting of four core solutions:


1. Predictive Modeling: Forecasting seasonal and non-linear ridership demand.
2. Interactive Dashboards: Real-time Power BI visualizations for operational and survey data.
3. Primary Research: A user engagement survey (n=257) to capture qualitative pain points.
4. Industry Benchmarking: Comparative analysis against Citi Bike (NYC) and BIXI (Montreal).


## 📊 Technical Methodology & Architecture

- Data Integration: Merged Toronto Open Data trip records with Environment Canada hourly weather data and station metadata using a structured SQL-based ETL process.
- Forecasting Models: Evaluated six models using RMSE, MAE, and MAPE metrics.
  - Top Performer: Facebook Prophet (MAPE: 0.0603) for balanced trend and seasonality.
  - Others: SARIMA, Holt-Winters, LSTM (Neural Networks), XGBoost, and Linear Regression.
- BI Stack: Built an integrated Power BI dashboard linking ridership trends directly to user feedback and weather fluctuations.


## 💡 Key Business Insights

- Demographics: Core users are young adults aged 25–34 (48%) and full-time workers (52.5%).
- Feature Demand: 33.8% of users requested baskets/storage, and 38.9% expressed interest in e-scooters.
- The Membership Gap: Toronto’s 10% membership contribution lags significantly behind NYC and Montreal (80%+).


## 🚀 Strategic Recommendations

- "WeBike2Gether" Campaign: A 3-month growth plan including referral programs, influencer partnerships, and community pop-ups to increase membership contribution to 40%.
- Smart Redistribution: Using predictive insights to rebalance stations, particularly focusing on transit hubs to improve first-mile/last-mile connectivity.
- Fleet Diversification: Introducing winter-ready bikes (studded tires) and cargo bikes to meet year-round demand.
