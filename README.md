# Harmonizing Multimodal Remote Sensing Data Processing

![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)

This repository provides a Python-based pipeline for processing and harmonizing multimodal, multi-resolution remote sensing data. The primary goal is to generate spatially-aligned data patches suitable for machine learning applications, directly addressing the challenges of working with diverse geospatial raster datasets.

## Overview

Integrating remote sensing data from different sensors (e.g., DEM, SAR, Optical) is challenging due to variations in spatial resolution, data types, and structures. This repository offers a solution by providing a robust workflow to create analysis-ready datasets without degrading data quality through resampling.

The core of this repository is the `test_patch_processing.ipynb` Jupyter Notebook, which provides a step-by-step demonstration of the entire pipeline.

### Key Features

* **Automated Data Setup:** Includes a script to automatically download and prepare the sample dataset from Zenodo.
* **Native Resolution Extraction:** Extracts data patches at their original resolutions, preserving data integrity and avoiding resampling artifacts.
* **Spatial Alignment:** Ensures that patches from different data sources are perfectly centered on the same geographic coordinate.
* **Clear Visualizations:** Provides functions to visualize the study area, patch locations, and the real-world footprints of the extracted data.

## The Data Processing Workflow

The pipeline follows a logical sequence of steps to transform raw, multi-resolution raster files into a harmonized set of patches.

1.  **Download & Prepare Data:** The initial step downloads the sample data from Zenodo, extracts it, and prepares it for use.
2.  **Define Study Area:** A vector shapefile is used to define the precise geographic boundary of the area of interest.
3.  **Generate Patch Centers:** A systematic grid of points is generated across the study area. These points are then filtered to keep only those within the defined boundary, ensuring all future patches are relevant.
4.  **Extract Aligned Patches:** For each valid center point, a data patch of a fixed pixel size (e.g., 224x224) is extracted from each raster source. This is done at the raster's native resolution.

## Getting Started

### Prerequisites

This project uses Python 3. Key libraries are listed below and should be included in a `requirements.txt` file:
* `rasterio`
* `geopandas`
* `matplotlib`
* `numpy`
* `requests`

### Installation

1.  Clone the repository:
    ```bash
    git clone [your-repo-link]
    cd [your-repo-name]
    ```
2.  Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```

### Running the Notebook

The `test_patch_processing.ipynb` notebook provides a complete demonstration of the data preparation pipeline.

1.  Launch Jupyter Notebook or JupyterLab.
2.  Open `test_patch_processing.ipynb`.
3.  Run the first code cell ("Step 0: Download and Prepare Data") to automatically download and extract the sample dataset.
4.  Run the subsequent cells to walk through the entire data processing workflow from start to finish.

## Data

A sample dataset is provided for demonstrating the pipeline. It can be downloaded automatically by running the notebook or manually from the following link:

* **URL:** [https://zenodo.org/records/15635067/files/harmonizing_multimodal_RMS.zip?download=1](https://zenodo.org/records/15635067/files/harmonizing_multimodal_RMS.zip?download=1)

The dataset contains pre-processed DEM, SAR, Optical, and Thermal raster files for the Pine Lake-Middle Salt Creek watershed.

## Context and Motivation

This data processing pipeline was developed in support of a larger research project, "Toward National-scale Hydrography Mapping: A Multimodal, Multitask Deep Learning Framework," at the University of Illinois Urbana-Champaign. It serves as the foundational step for preparing data for advanced deep learning models.

## Author

* **Nattapon Jaroenchai** - *Department of Geography and Geographic Information Science, University of Illinois Urbana-Champaign*

## License

This project is licensed under the MIT License - see the `LICENSE.md` file for details.
