# Predictive Maintenance of EV Charging Stations

This repository contains a project developed in partial fulfillment of the requirements for the Big Data Analytics course offered by the Master of Science in Business Analytics program at the Carlson School of Management, University of Minnesota.

## Project Overview

As EV adoption rises, maintaining a reliable charging infrastructure becomes critical. In this project, we built a predictive maintenance framework using big data tools like Apache Spark, Pandas, and machine learning algorithms (XGBoost, GBT) to forecast the "days till breakdown" of charging stations based on weather and operational data.

Additionally, we visualized the model results using KeplerGL, producing an interactive geographic map that displays charger locations colored by their predicted risk levels.

## Key Components

- Weather risk scoring using OpenWeather API
- Feature engineering and normalization
- Model training with XGBoost and Spark MLlib
- Risk-based scoring of each charger station
- Geospatial visualization with KeplerGL to identify high-risk stations geographically
- Deployment-ready predictive framework
- Visualizations and model evaluation metrics

## Deliverables

- Predictive risk scores and "days till breakdown" for each EV charging station
- An interactive map dashboard showing station risks visually using KeplerGL
- Codebase for big data processing and modeling pipelines

## Visualizations

**Predicted Risk Map (KeplerGL):**

![KeplerGL Map](visualizations/KeplerGL%20output.jpg)

**Another model visualization:**

![KeplerGL Map](visualizations/KeplerGL%20output2.jpg)


## Important Links

- [OpenWeather API Documentation](https://openweathermap.org/api)
- [KeplerGL Visualization Tool](https://kepler.gl/)

---

> **Note:**  
> This project repository is created in partial fulfillment of the requirements for the Big Data Analytics course offered by the Master of Science in Business Analytics program at the Carlson School of Management, University of Minnesota.

---
