# Rainfall Onset Validation with CHIRPS Daily Data (Ibadan, Nigeria)

## Overview
This project evaluates a simple rainfall onset rule using historical daily rainfall observations from **CHIRPS** for **Ibadan, Nigeria** across **2021–2023**.

The notebook loads NetCDF rainfall files, extracts rainfall values for Ibadan, explores the time series, applies an onset detection rule, and performs a validation step to check whether detected onset dates represent sustained rainfall conditions.

## Goal
Test whether a rainfall onset rule can reliably identify the beginning of the rainy season from observed rainfall data.

## Method

### 1. Load and combine CHIRPS rainfall data
- Read multiple NetCDF (`.nc`) files
- Merge them into a single dataset using `xarray`

### 2. Extract Ibadan rainfall records
Coordinates used:
- Latitude: `7.3775`
- Longitude: `3.9470`

### 3. Prepare and inspect the data
- Convert to a pandas DataFrame
- Sort by date
- Check for missing values
- Generate rainfall plots and summary statistics

### 4. Detect rainfall onset
Rule used:
- Calculate a **3‑day rolling rainfall total**
- Mark the **first date each year where rainfall ≥ 20 mm**

### 5. Validate onset dates
Apply a post-check:
- Inspect the following **10 days**
- Use dry‑spell filtering
- Reject weak onset signals

## Outputs
The notebook generates:
- Rainfall visualizations
- Summary statistics
- `summary_statistics.xlsx`
- `onset_dates.xlsx`

## Tech Stack
- Python
- pandas
- xarray
- numpy
- matplotlib
- dask

## Repository Structure
```
project/
├── project-validation.ipynb
├── README.md
├── *.nc
├── onset_dates.xlsx
└── summary_statistics.xlsx
```

## Run Locally

```bash
pip install pandas numpy matplotlib xarray dask
jupyter notebook
```

Open:

```text
project-validation.ipynb
```

## Notes
This project is intended as an exploratory validation workflow and can be extended with additional years, alternative onset definitions, or comparison against meteorological benchmarks.
