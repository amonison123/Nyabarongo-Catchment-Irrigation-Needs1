# Evaluating Climate Trends and Irrigation Requirements in Rwanda's Nyabarongo River Catchment

This repository contains the complete computational pipeline for the Master of Science dissertation: 
**"Evaluating Historical and Future Precipitation Trends for Irrigation Needs in Rwanda's Nyabarongo River Catchment Using Earth System Models"** (University of Rwanda).

## Project Overview
This study leverages high-resolution, bias-corrected Earth System Model projections from the Coupled Model Intercomparison Project Phase 6 (CMIP6; ACCESS-CM2) to model future climate extremes (ETCCDI indices) and evaluate irrigation needs for maize, beans, and cassava through 2050. Evapotranspiration is modeled programmatically using the FAO-56 Penman-Monteith equation, integrated with a 30m NASA SRTM Digital Elevation Model (DEM) for precise localized pressure adjustments.

## Analytical Workflow
The modeling pipeline is divided into four chronological Jupyter Notebooks:
1. **`dataextraction.ipynb`**: Programmatically extracts and clips NASA NEX-GDDP-CMIP6 climate data, CHIRPS satellite estimates, and historical station data to the Nyabarongo catchment bounding box.
2. **`Model_Validation.ipynb`**: Evaluates the historical performance of the ACCESS-CM2 model against observed ground station data using statistical metrics (R-squared, RMSE, Bias).
3. **`Climate_Extremes_Analysis.ipynb`**: Calculates ETCCDI extremes (Consecutive Dry Days and Maximum 5-Day Rainfall) and generates spatial projection maps for SSP2-4.5 and SSP5-8.5 scenarios.
4. **`Crop_Water_Requirements.ipynb`**: Implements the FAO-56 Penman-Monteith thermodynamic equations, computes crop-specific water requirements, and formulates Net Irrigation Water Requirements (NIWR) under baseline and future scenarios.

## Important Note on Reproducibility and File Paths
The Jupyter Notebooks in this repository were originally executed on a local workstation using a "flat" directory structure. File input and output directories are currently configured using absolute local paths (e.g., `C:\Users\Baikania Amonison\Desktop\final data extraction and analysis\`).

To successfully reproduce this analysis and run the notebooks on your local machine, you have two options:

**Option 1: Mirror the Original Folder Structure (Easiest)**
1. Place all Jupyter Notebooks, raw NetCDF files, historical CSV datasets, and shapefiles directly into a single main folder.
2. Create a subfolder named `Thesis_Outputs` within that main folder to receive the generated visualizations and tables.
3. Open each notebook and update the `base_dir` variable in the first code cell to point to your new main folder path.

**Option 2: Use a Modular Structure**
If you organize the files into subfolders (e.g., `data/raw`), you must manually update the absolute paths within the `pd.read_csv()`, `.to_csv()`, and `plt.savefig()` functions in every notebook to match your new directory layout.

## Setup & Installation
To run these notebooks locally, clone this repository and install the required dependencies:

```bash
git clone [https://github.com/amonison/Nyabarongo-Catchment-Irrigation-Needs.git](https://github.com/amonison/Nyabarongo-Catchment-Irrigation-Needs.git)
cd Nyabarongo-Catchment-Irrigation-Needs
pip install -r requirements.txt