Title
Deforestation and Vegetation Analysis (2000–2023) around study centroid in Ucayali, Peru

Overview
This project analyzes:

Tree cover loss from 2008–2022 using the Hansen Global Forest Change dataset (v1.10, 2022 release).
Vegetation status in 2023 using Sentinel‑2 imagery (false color composite and NDVI).
The analyses were implemented in Google Earth Engine (GEE) and exported for mapping in GIS software (e.g., QGIS/ArcGIS) and for reporting (PDF slides).

Study Area

Centroid: [-75.54133, -8.59263] (Ucayali, Peru)
Study area: 25 km radius buffer around the centroid (≈ 1,963 km²)
Geometry created in GEE (and also exported as a shapefile for external GIS use)
Data Sources

Tree Cover Loss: Hansen Global Forest Change 2022 v1.10 (UMD/hansen/global_forest_change_2022_v1_10)
Reference: Hansen et al. (2013), Science, updated annually.
Global Forest Watch Data Portal: https://data.globalforestwatch.org/documents/tree-cover-loss/explore
Sentinel‑2 Surface Reflectance: COPERNICUS/S2_SR_HARMONIZED (2023)

Methods

1. Tree Cover Loss (2008–2022)
Dataset: UMD/hansen/global_forest_change_2022_v1_10
Band used: lossyear (1–22 => 2001–2022)
Workflow (GEE):
Build a 25 km buffer from centroid
Clip lossyear to buffer
Visualize 2008–2022 (lossyear 8–22) with a sequential color palette
Compute areas (hectares) for:
2021 (lossyear = 21)
2021–2022 (lossyear = 21 or 22)
2008–2022 (lossyear = 8–22)

2. Vegetation Analysis (2023)
Dataset: COPERNICUS/S2_SR_HARMONIZED
Date range: 2023-01-01 to 2023-12-31
Filters: CLOUDY_PIXEL_PERCENTAGE < 20
Workflow (GEE):
Create a 2023 median composite and clip to buffer
False color composite (B8, B4, B3) to emphasize vegetation
Compute NDVI = (B8–B4)/(B8+B4)
Classify NDVI into:
Water (< 0)
Bare soil/urban (0–0.2)
Sparse vegetation (0.2–0.4)
Moderate vegetation (0.4–0.7)
Dense vegetation (>= 0.7)
