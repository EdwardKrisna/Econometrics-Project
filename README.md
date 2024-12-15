# Spatially Granular Poverty Index (SGPI) Research

This repository contains research on developing a Spatially Granular Poverty Index (SGPI) for urban poverty mapping in Bali, Indonesia using remote sensing satellite imagery and geospatial big data.

## Project Overview

The research aims to develop an innovative approach to urban poverty mapping by:
- Integrating multiple sources of satellite imagery and geospatial data
- Creating a high-resolution (1km) poverty index
- Validating results against official poverty statistics
- Providing an inexpensive and scalable methodology for poverty monitoring

## Data Sources

The research utilizes the following data sources:

### Satellite Imagery
- Sentinel-2 (for NDVI and NDBI calculation)
- Sentinel-5P (for NO2 and CO pollution levels)
- MODIS (for Land Surface Temperature)
- VIIRS (for Nighttime Light intensity)

### Points of Interest (POI)
- Education facilities
- Healthcare facilities 
- Economic activity locations

### Reference Data
- Official poverty statistics from Statistics Indonesia (BPS)
- Administrative boundary data

## Methodology

The research methodology consists of several key steps:

1. **Data Collection and Preprocessing**
   - Satellite imagery acquisition through Google Earth Engine
   - POI data collection from OpenStreetMap
   - Creation of 1km analysis grid

2. **Feature Extraction**
   - Calculation of vegetation indices (NDVI)
   - Built-up area indices (NDBI)
   - Air pollution metrics
   - Distance calculations to POIs

3. **SGPI Construction**
   Three different weighting approaches were tested:
   - Equal Weighted Sum (EWS)
   - Pearson Correlation Coefficient Weighted Sum (PCCWS)
   - PCA Weighted Sum (PCAWS)

   Each approach was combined with three data transformation methods:
   - Min-max scaling
   - Standard scaling
   - Yeo-Johnson transformation

4. **Validation and Analysis**
   - Correlation analysis with official poverty data
   - Statistical validation including OLS regression
   - Spatial autocorrelation analysis
   - Cross-validation and bootstrapping

## Key Findings

- The Equal Weighted Sum method with Yeo-Johnson transformation (EWS-YJ) showed the strongest performance
- Correlation coefficient with official poverty rate: 0.737
- Strong spatial autocorrelation (Moran's I: 0.971, p-value: 0.001)
- Cross-validation results indicate some instability in model performance
- Bootstrap analysis provides confidence intervals for parameter estimates

## Repository Structure

```
├── data/
│   ├── satellite/         # Satellite imagery data
│   ├── poi/              # Points of interest data
│   └── reference/        # Administrative boundaries and poverty data
├── scripts/
│   ├── data_collection/  # Google Earth Engine scripts
│   ├── preprocessing/    # Data preparation scripts
│   └── analysis/        # Statistical analysis scripts
├── results/
│   ├── maps/            # Generated poverty maps
│   └── statistics/      # Statistical output
└── documentation/       # Additional documentation and methodology details
```

## Requirements

### Python Dependencies
- pandas
- numpy
- scikit-learn
- geopandas
- rasterio
- folium
- statsmodels
- earthengine-api
- matplotlib
- seaborn

### External Requirements
- Google Earth Engine account
- Access to satellite imagery APIs
- OpenStreetMap data access

## Limitations and Future Work

- Current implementation limited to Bali region
- Temporal analysis could be expanded
- Additional validation with ground truth data needed
- Potential for incorporation of additional data sources
- Opportunities for methodology refinement
