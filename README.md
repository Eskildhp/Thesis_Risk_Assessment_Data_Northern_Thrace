# A GIS Framework for Risk Management of Immovable Cultural Heritage in Northern Thrace

This repository contains supporting material for the master's thesis *A GIS Framework for Risk Management of Immovable Cultural Heritage: A Case Study in Northern Thrace (Southern Bulgaria)*.

The study develops a GIS-based regional framework for assessing relative archaeological risk by combining environmental hazards with archaeological site vulnerability. The assessment includes seismic hazard, flooding, wildfire, landslide susceptibility and soil erosion. Archaeological sites are grouped according to similar environmental conditions before cluster-specific Analytic Hierarchy Process (AHP) weighting is applied.

The resulting criterion weights are combined with standardized risk variables using Weighted Linear Combination (WLC). The archaeological risk scores are evaluated using Getis-Ord Gi* hot spot analysis. The robustness of the model is evaluated using One-at-a-Time (OAT) sensitivity analysis and Monte Carlo uncertainty analysis.

## Repository contents

The repository contains supporting material used to document the analytical workflow of the thesis, including:

- a public version of the archaeological site master dataset
- scripts and documentation for environmental data acquisition
- environmental clustering inputs, outputs and visualizations
- cluster-specific AHP matrices, comparison evidence and supporting calculations
- archaeological risk-assessment data and WLC results
- OAT sensitivity analysis inputs, scripts and results
- Monte Carlo uncertainty analysis inputs, scripts and results
- documentation describing the analytical procedures and files

Original source datasets are identified in the thesis and supporting documentation. In cases where third-party datasets are not redistributed, source and access information or derived analytical data are provided instead.

## Analytical workflow

The main analytical steps are:

1. Environmental and archaeological data preparation
2. Environmental spatial clustering
3. Cluster-specific Analytic Hierarchy Process (AHP)
4. Weighted Linear Combination (WLC)
5. Getis-Ord Gi* hot spot analysis
6. One-at-a-Time (OAT) sensitivity analysis
7. Monte Carlo uncertainty analysis

## Repository structure

The repository is organized according to the main stages of the analytical workflow.

    Thesis_Risk_Assessment_Data_Northern_Thrace/
    ├── README.md
    ├── LICENSE
    ├── .gitignore
    │
    ├── data/
    │   ├── README.md
    │   └── Sites_master.csv
    │
    ├── data_acquisition/
    │   ├── README.md
    │   └── scripts/
    │       └── Copernicus_DEM_download.ps1
    │
    ├── clustering/
    │   ├── README.md
    │   ├── ward_clustering_ruslog.py
    │   ├── Cluster_matrix_Ruslog.csv
    │   ├── results/
    │   └── visualization/
    │
    ├── AHP/
    │   ├── README.md
    │   ├── matrices/
    │   ├── evidence/
    │   └── results/
    │
    ├── risk_assessment/
    │   ├── README.md
    │   └── results/
    │
    ├── sensitivity_analysis/
    │   ├── README.md
    │   ├── inputs/
    │   ├── scripts/
    │   └── results/
    │
    └── uncertainty_analysis/
        ├── README.md
        ├── inputs/
        ├── scripts/
        └── results/

Each analytical folder contains its own README with more detailed information about the procedure, files and outputs.

## Data

The `data/` folder contains the public site-level master dataset used throughout the thesis workflow.

`Sites_master.csv` contains archaeological, descriptive, environmental and analytical attributes for the 250 archaeological sites included in the final analysis.

Precise archaeological site coordinates are not included in the public dataset.

## Data acquisition

The `data_acquisition/` folder contains documentation and scripts relating to the acquisition of external environmental datasets.

The included PowerShell script was used to identify and download Copernicus DEM tiles overlapping the study area through the Copernicus Data Space Ecosystem.

Original third-party environmental datasets are not necessarily redistributed through this repository and remain subject to the terms and conditions of the respective data providers.

## Environmental spatial clustering

The `clustering/` folder contains the Ward hierarchical clustering workflow used to group archaeological sites according to similarities in their environmental characteristics.

The folder includes:

- the transformed clustering matrix
- the Ward hierarchical clustering Python script
- cluster solutions containing three to seven clusters
- silhouette score and cluster-size evaluation
- environmental profiles of the candidate and selected clusters
- full and truncated Ward dendrograms
- a parallel boxplot showing the environmental characteristics of the final three-cluster solution

Detailed information is provided in `clustering/README.md`.

## Analytic Hierarchy Process

The `AHP/` folder contains the three cluster-specific AHP models used to derive criterion weights.

It includes:

- the completed pairwise comparison matrices for Clusters 1, 2 and 3
- the evidence worksheet used to support the pairwise comparisons
- calculated criterion weights
- consistency calculations and summary results

Detailed information is provided in `AHP/README.md`.

## Risk assessment

The `risk_assessment/` folder contains the final site-level Weighted Linear Combination results.

The results include the standardized criterion scores, cluster assignment, final WLC archaeological risk score and categorical risk classification for each archaeological site.

Detailed information is provided in `risk_assessment/README.md`.

## OAT sensitivity analysis

The `sensitivity_analysis/` folder contains the One-at-a-Time sensitivity analysis used to evaluate how changes in individual AHP pairwise comparisons influence the archaeological risk results.

For each environmental cluster, individual pairwise comparisons were changed by one adjacent level on the Saaty scale while the remaining comparisons were kept unchanged. Criterion weights, consistency ratios, WLC scores and risk classifications were recalculated after each perturbation.

The folder contains the analysis script, public input data, baseline weights, pairwise sensitivity runs, site-level results and criterion-level sensitivity summaries.

Detailed information is provided in `sensitivity_analysis/README.md`.

## Monte Carlo uncertainty analysis

The `uncertainty_analysis/` folder contains the Monte Carlo analysis used to evaluate uncertainty associated with the cluster-specific AHP criterion weights.

Each baseline criterion weight was independently varied by ±10% and the resulting weights were normalized to sum to one. The WLC risk scores were recalculated for 1,000 simulations per environmental cluster.

The outputs include baseline validation, simulation weights, site-level uncertainty statistics, cluster summaries, convergence results and classification stability.

Detailed information is provided in `uncertainty_analysis/README.md`.

## Data availability

This repository contains derived analytical data, scripts, supporting tables and documentation used in the thesis.

Environmental and spatial data originate from external providers including Copernicus, the European Commission Joint Research Centre, EFEHR, EMSC, EMODnet and other European data infrastructures. Original datasets remain subject to the terms and conditions of the respective providers.

Precise archaeological site coordinates are not included in the public repository. Transformed or derived spatial variables are provided where required for the analyses. For example, `C_x` and `C_y` in the environmental clustering data are transformed analytical variables and should not be interpreted as original archaeological site coordinates.

## Reproducibility

The purpose of the repository is to make the analytical workflow and supporting results of the thesis transparent and inspectable.

GIS data preparation and spatial analysis were primarily carried out in ArcGIS Pro. Python was used for environmental clustering, sensitivity analysis, Monte Carlo uncertainty analysis and supporting data-processing tasks. A Windows PowerShell script was used for Copernicus DEM data acquisition.

Individual folders contain README files describing their inputs, outputs, software requirements and analytical procedures.

## Thesis

*A GIS Framework for Risk Management of Immovable Cultural Heritage: A Case Study in Northern Thrace (Southern Bulgaria)*

Master's thesis  
Digital Heritage and Landscape Archaeology  
Department of History and Archaeology  
University of Cyprus  
2026
