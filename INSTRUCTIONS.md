# Instructions for Running the Predictive Maintenance Project

This document provides setup and usage instructions for the Predictive Maintenance of EV Charging Stations project.

---

## Environment Setup

1. **Python Version:**  
   Python 3.8 or later

2. **Install Required Libraries:**

```bash
pip install pandas numpy aiohttp tqdm scikit-learn xgboost pyspark keplergl
```

(Optional: Install Jupyter if you don't have it)

```bash
pip install notebook
```

---

## Project Structure

- `Trends EV analysis.ipynb` → Main Jupyter Notebook containing all project steps: data enrichment, feature engineering, modeling, and visualization
- `README.md` → Project overview
- `INSTRUCTIONS.md` → This instruction file
- `visualizations/` → Folder for KeplerGL maps (optional if saving)
- `data/` → (Optional) sample CSV outputs if needed

---

## How to Run

### 1. Open the Notebook

Simply open `Trends EV analysis.ipynb` in JupyterLab, Jupyter Notebook, or any compatible editor (e.g., VS Code with Jupyter extension).

```bash
jupyter notebook Trends\ EV\ analysis.ipynb
```

### 2. Set API Key

Make sure you set your OpenWeather API key correctly inside the notebook where weather data enrichment is called.

### 3. Run All Cells Sequentially

The notebook is organized in the following order:
- Load station data
- Enrich with weather risk scores (async requests)
- Feature engineering (usage intensity, connector density, etc.)
- Create synthetic target variable (`days_to_breakdown`)
- Train XGBoost and Spark GBT models
- Evaluate model (RMSE, MAE, R²)
- Create KeplerGL visualization

### 4. Saving Output (optional)

Export final enriched data:

```python
data_ev_final.to_csv('final_ev_charger_risk.csv', index=False)
```

or on Databricks:

```python
df_final.write.csv('/dbfs/FileStore/final_ev_charger_risk.csv', header=True)
```

## How to Load CSV into KeplerGL for Visualization

After exporting `final_ev_charger_risk.csv`, you can visualize it easily:

```python
from keplergl import KeplerGl
import pandas as pd

# Load the exported CSV
data = pd.read_csv('final_ev_charger_risk.csv')

# Create a KeplerGL map
map_ = KeplerGl()
map_.add_data(data=data, name="EV Charging Stations Risk")
map_
```

In KeplerGL:
- Set `Latitude` and `Longitude` fields for mapping.
- Color-code or size the points based on the `weather_risk_score` or `days_to_breakdown`.


---

## Notes
- Only small sample data is committed here

---

> **Reminder:**  
> This project repository is created in partial fulfillment of the requirements for the Big Data Analytics course offered by the Master of Science in Business Analytics program at the Carlson School of Management, University of Minnesota.
