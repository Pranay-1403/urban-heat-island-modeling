# Urban Heat Island (UHI) Spatial Modeling & Green Space Cooling Simulation

An end-to-end geospatial machine learning pipeline designed to quantify urban heat island intensity, benchmark predictive algorithms against satellite-derived surface temperatures, and simulate the localized cooling effects of strategic green canopy interventions across Hyderabad, India.

---

## 🗺️ Live Interactive Map

Explore the full spatial analysis, surface temperature hotspots, and street-level intervention points directly in your browser:

👉 **[Launch Interactive Hyderabad Heat Map](https://Pranay-1403.github.io/urban-heat-island-modeling/hyderabad_urban_heat_map.html)**


---

## Project Overview

Rapid urban expansion drives localized temperature spikes due to asphalt, concrete density, and diminished vegetation canopy. This project integrates multitemporal satellite imagery from Landsat 8/9 to:
1. Extract calibrated physical land metrics (Land Surface Temperature, NDVI, NDBI).
2. Train and evaluate linear vs. non-linear regression models predicting microclimate thermal intensity.
3. Simulate targeted urban greening scenarios across high-risk heat stress zones.
4. Export an interactive web map identifying micro-hotspots overlaid directly on street networks.

---

## Key Results & Findings

- *Model Benchmark:* Random Forest Regressor substantially outperformed classical linear models by capturing complex non-linear spatial interactions.
  - *Random Forest:* $R^2 = 0.3196$ | $\text{MAE} = 3.77^\circ\text{C}$ | $\text{RMSE} = 5.55^\circ\text{C}$
  - *Linear Regression:* $R^2 = 0.2137$ | $\text{MAE} = 4.19^\circ\text{C}$ | $\text{RMSE} = 5.97^\circ\text{C}$
- *Feature Significance:* Engineered indices drive the vast majority of temperature variation:
  - *NDVI (Vegetation Index):* ~34% feature importance
  - *NDBI (Built-up Index):* ~31% feature importance
  - Combined, green canopy and concrete density account for over *65% of predictive power* over raw spectral bands.
- *Cooling Intervention Simulation:*
  - Simulating an increase in vegetation canopy (+0.30 NDVI) across the top 15% hottest urban zones yielded an *average surface temperature reduction of 8.08°C*.
  - Peak localized cooling reached up to *15.58°C* in high-density built environments.

---

## Tech Stack

- *Geospatial Processing:* rasterio, geopandas, pyproj
- *Machine Learning & Modeling:* scikit-learn (Linear Regression, Ridge, Random Forest)
- *Data Analysis & Visualization:* pandas, numpy, matplotlib, folium
- *Data Source:* USGS EarthExplorer — Landsat 8-9 OLI/TIRS Collection 2 Level-2

---

## Methodology Pipeline

```text
[ Landsat 8/9 Bands (Red, NIR, SWIR, ST_B10) ]
                      │
                      ▼
[ Radiometric Calibration & Scale Conversion (DN -> Reflectance / °C) ]
                      │
                      ▼
[ Feature Engineering: NDVI & NDBI Calculations ]
                      │
                      ▼
[ Tabular Preprocessing & Outlier Filtering (Pandas) ]
                      │
                      ▼
[ Model Training & Evaluation (Linear vs. Ridge vs. Random Forest) ]
                      │
                      ▼
[ Policy Simulation: Green Space Addition on 85th Percentile Hotspots ]
                      │
                      ▼
[ Geospatial Coordinate Projection & Folium Interactive Map Export ]

```





## Setup & Execution

1. Clone the repository
git clone  https://github.com/Pranay-1403/urban-heat-island-modeling.git
cd urban-heat-island-modeling

2. Install dependencies
pip install -r requirements.txt


3. Data Acquisition
​Download the following Level-2 products for Path 144 / Row 048 from USGS EarthExplorer:
​SR_B4.TIF (Red)
​SR_B5.TIF (Near-Infrared)
​SR_B6.TIF (Shortwave Infrared 1)
​ST_B10.TIF (Surface Temperature)
​Place these files in data/raw/ or your notebook directory.