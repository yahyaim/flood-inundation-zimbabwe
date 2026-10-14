# Flood Inundation Maps in Zimbabwe: Intelligent Modelling Using Python

Final-year research project (University of Southampton, Electronics and Computer Science).

## Problem
Flood inundation mapping is under-studied in countries like Zimbabwe because
river and water-level data are limited. This project builds a framework that works
from publicly available data.

## Approach
1. Data: monthly precipitation and temperature (CRU TS, 1901-2020) and monthly
   discharge (ADHI database, 1950-2018). 82 hydrometric stations in Zimbabwe.
2. Exploratory analysis: anomaly detection with Isolation Forest.
3. Hydrologic modelling: a PIHM-style water balance to compute the change in
   water level (dH/dt), used as the target for the ML models.
4. Machine learning: Random Forest and Multilayer Perceptron forecast dH/dt,
   tuned with grid search and k-fold cross-validation.
5. Mapping: flood maps for the Sanyati River (Lake Kariba) built in QGIS from SRTM
   elevation data and the Terrain Ruggedness Index.

## Results
| Model | MAE | MSE | Training time |
|---|---|---|---|
| Random Forest | 0.00443 | 0.00373 | ~1.5 hours |
| MLP | 0.07434 | 0.13000 | ~72 hours |

Random Forest clearly outperformed the MLP, which failed to model the change in
water depth in this setup.

## Limitations
- The hydrologic model uses monthly averages and several assumptions, and could
  not be calibrated against real flood events.
- The QGIS maps are high resolution, but their accuracy is uncertain.
- The MLP was limited by training time and hyperparameter search.

## Tools
Python (pandas, scikit-learn, Keras, Plotly, Seaborn), QGIS.

## Data
Not included. Sources: CRU TS (Harris et al., 2020) and ADHI (Tramblay and Rouche, 2020).
