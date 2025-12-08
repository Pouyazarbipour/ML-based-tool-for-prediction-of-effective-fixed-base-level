# ML-based tool for prediction of effective fixed base level

Welcome to The XGBoost Building Base Level Prediction Tool, a GUI-based applicatio developed using machine learning and the XGBoost method. This tool provides accurate and efficient predictions of displacement (mm) in buildings with deep retaining walls, which helps determine the effective fixed-base level based on a comprehensive dataset and carefully selected input parameters related to soil-structure interaction (SSI).

## Overview

This project is designed to predict the displacement of basement levels in reinforced concrete buildings under seismic loads, aiding in the determination of the base level according to Iran's Seismic Design Code (Standard 2800). The model uses a dataset split into 70% for training, 15% for validation, and 15% for testing, achieving R-squared statistics of 0.99 for training and 0.97 for testing. For more details, refer to the article by Zarbipour et al. (2026).

![Main Page GUI](https://github.com/Pouyazarbipour/The-XG-Boost-Berm-Breakwater-Recession-Prediction-tools/blob/main/GUI%20pic/main_page.JPG)

## Data Range and Parameters

The model uses the following input parameters, categorized into categorical and numerical features. These are derived from Opensees simulations, soil properties, and structural details for square and rectangular plans across three soil types (Hand, Clay, Sand).

### Categorical Features

* **Soil_type**: Dasti (manual soil), Clay, Sand
* **Plan_type**: Square, Rectangular

### Numerical Features (approximate data ranges)

* **Gamma (γ, kN/m³)**: 14 – 19.7
* **K0** (at-rest earth pressure coefficient): 0.44 – 0.631
* **Lateral_SP (kN/m²)**: 25 – 106
* **NF (kN)**: 200 – 2,544 (normal force between wall and soil)
* **FF (kN)**: 62 – 895 (frictional force between wall and soil)
* **Wall_thick (cm)**: 5 – 20
* **H (m)**: 3.2 – 9.6 (basement height/depth)
* **CSC (kg/m²)**: 25 (concrete strength; fixed)
* **P (kN)**: −250 – 250 (axial force from ETABS)
* **V2 (kN)**: −250 – 0
* **V3 (kN)**: −120 – 120

### Target (Output)

* **Dis**: 0.01 – 3.1 mm
  Displacement of basement stories, used to identify the effective fixed-base level where:
  Dis ≤ 0.02 × first-floor displacement.

## Model and Prediction Approach

The XGBoost method was chosen for its high predictive accuracy and efficiency with large datasets, particularly suited for regression tasks and capturing complex non-linear relationships. A Bootstrap approach is employed to estimate prediction uncertainty by repeatedly sampling the training data with replacement and training multiple XGBoost models. The standard deviation of the predictions quantifies variability, and a 95% confidence interval is calculated as `prediction ± 1.96 × standard deviation`. An upper bound prediction (`prediction + standard deviation`) is also provided for conservative estimates, approximately at the 84th percentile.

For detailed guidance, refer to the [User & Technical Manual](https://coastalhydlab.ir/software/xgb-bbrp/manual).

## Downloads

- [Download the Software](https://drive.google.com/file/d/1xDbzpUAMEwoJ3jnKcOECaG23iwRccPXW/view?usp=sharing)
- [Download User & Technical Manual](https://drive.google.com/file/d/1xDbzpUAMEwoJ3jnKcOECaG23iwRccPXW/view?usp=sharing)

## About

Programmed by Pouya Zarbipour. For questions or feedback, please contact [pouyazarbipour@gmail.com](mailto:pouyazarbipour@gmail.com).

## Disclaimer

This tool aims to improve prediction of effective fixed base level and enhance design reliability. Please refer to the User & Technical Manual for information on intended use and limitations.
