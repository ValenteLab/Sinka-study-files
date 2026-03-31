# A Landsat-based Alternative to Adaptive Management

This repository contains geospatial data, model objects, and R scripts used to develop and evaluate a Landsat-based land cover prediction workflow as an alternative to traditional adaptive management approaches.

The purpose of this code is to replicate the analyses associated with the manuscript:

Abubakar, S.K., N. Lana, and J.J. Valente. (in review). A Landsat-Based Alternative for Adaptive Habitat Management on Protected Lands. PLOS ONE.

The project integrates Landsat imagery, NLCD land cover data, tree canopy cover data, and field-collected training and validation data to train and apply a Random Forest machine learning model for land cover classification and prediction across Wildlife Management Areas (WMAs) in Alabama. The goal of the project is to evaluate whether freely available geospatial data, particularly Landsat imagery, can be used to generate reliable land cover predictions that support traditional adaptive management monitoring approaches.

---

## Data Description

### Remote Sensing Data
- **Landsat imagery (2008 and 2024)** used to derive spectral predictors for classification (see `LandsatData.xml` for metadata).
- Raster stacks (`StackedPredictors.tif`, `2008StackedPredictors.tif`) contain processed spectral bands, derived indices and ancillary data used as model inputs (see `PredictorsStack.xml` for metadata).

### Land Cover and Environmental Layers 
(Used as additional predictor variables in the classification workflow.)
- **NLCD 2024** (see `NLCDData.xml` for metadata).
- **Tree Canopy Cover (TCC 2021)** (see `TCC.xml` for metadata).

### Vector Data
- **trainingData.shp**: Field-collected land cover data used to train and validate the model (see `TrainingAndValidationData.xml` for metadata).
- **studyArea.shp**: Boundary polygon defining the spatial extent of the analysis (see `WMAsShapefile.xml` for metadata)..

---

## Scripts and Workflow

### 1. Model Training
`landcoverModelScript.Rmd` performs:
- Raster preprocessing and stacking
- Extraction of raster values at training locations
- Training of a Random Forest classifier
- Model evaluation and validation
- Saving the trained model as `rf_model.RData`

### 2. Prediction
`PredictionScript.Rmd`:
- Loads the trained model
- Applies the model to predictor rasters
- Generates spatially explicit land cover predictions across the study area

