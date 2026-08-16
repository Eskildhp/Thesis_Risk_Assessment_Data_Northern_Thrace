# A GIS Framework for Risk Management of Immovable Cultural Heritage in Northern Thrace

This repository contains supporting material for the master's thesis *A GIS Framework for Risk Management of Immovable Cultural Heritage: A Case Study in Northern Thrace (Southern Bulgaria)*.

The study develops a GIS-based regional framework for assessing relative archaeological risk by combining environmental hazards with archaeological site vulnerability. The assessment includes seismic hazard, flooding, wildfire, landslide susceptibility and soil erosion. Archaeological sites are grouped according to similar environmental conditions before cluster-specific Analytic Hierarchy Process (AHP) weighting is applied. The resulting criterion weights are combined with standardized risk variables using Weighted Linear Combination (WLC).

The resulting archaeological risk scores are evaluated using Getis-Ord Gi\* hot spot analysis. The robustness of the model is evaluated using One-at-a-Time (OAT) sensitivity analysis and Monte Carlo uncertainty analysis.

## Repository contents

The repository contains supporting material used to document the analytical workflow of the thesis, including:

* Python scripts used for data processing and analysis
* Derived environmental and archaeological data used in the analyses
* Environmental clustering inputs, outputs and visualizations
* Cluster-specific AHP matrices and supporting calculations
* Archaeological risk-assessment data and analytical outputs
* OAT sensitivity analysis inputs and results
* Monte Carlo uncertainty analysis inputs and results
* Documentation describing the analytical procedures and files

Original source datasets are identified in the thesis and supporting documentation. In cases where third-party datasets may not be redistributed, the source and access information or derived data are available instead.

## Analytical workflow

The main analytical steps are:

1. Environmental and archaeological data preparation
2. Environmental spatial clustering
3. Cluster-specific Analytic Hierarchy Process (AHP)
4. Weighted Linear Combination (WLC)
5. Getis-Ord Gi\* hot spot analysis
6. One-at-a-Time (OAT) sensitivity analysis
7. Monte Carlo uncertainty analysis

## Repository structure

The repository is organized based on analytical component. The individual folders contain scripts, input or derived data, analytical results and documentation.

```text
Thesis_Risk_Assessment_Data_Northern_Thrace/
├── README.md
├── LICENSE
└── clustering/
    ├── README.md
    ├── ward_clustering_ruslog.py
    ├── Cluster_matrix_Ruslog.csv
    ├── results/
    └── visualization/
```

Additional analytical folders and supporting material will be added as the repository is completed.

## Environmental spatial clustering

The `clustering/` folder contains the environmental Ward hierarchical clustering workflow used to group the archaeological sites according to similarities in the environmental characteristics.

The folder includes:

* The transformed clustering matrix
* The Ward hierarchical clustering Python script
* Cluster solutions containing three to seven clusters
* Silhouette score and cluster size evaluation
* Environmental profiles of the potential and selected clusters
* Full and truncated Ward dendrograms
* A parallel box plot showing the environmental characteristics of the final three-cluster solution

Detailed information on the clustering procedure, file structure, software implementation and outputs is provided in [`clustering/README.md`](clustering/README.md).

## Data availability

This repository contains derived analytical data, scripts, supporting tables and documentation used in the thesis.

Environmental and spatial data come from external sources including European and national data providers. Original datasets are subject to the terms and conditions of the respective providers. In cases where redistribution is not allowed or possible, the repository includes information that identifies the original source with relevant processing information or derived analytical files.

Precise archaeological site coordinates are not included in the public repository. Transformed or derived spatial variables are provided instead. For example, `C_x` and `C_y` in the environmental clustering data are transformed analytical variables and should not be interpreted as original archaeological site coordinates.

## Reproducibility

The purpose of the repository is to make the analytical workflow and supporting results of the thesis transparent and inspectable and to enable the computational steps to be reproduced without the original data.

GIS data preparation and spatial analysis were primarily carried out in ArcGIS Pro. Python was used for environmental clustering, sensitivity analysis, Monte Carlo uncertainty analysis and supporting data-processing tasks.

Individual folders have their own README files describing the inputs, outputs, software dependencies and analytical procedures.

## Thesis

**A GIS Framework for Risk Management of Immovable Cultural Heritage: A Case Study in Northern Thrace (Southern Bulgaria)**

Master's thesis  
Digital Heritage and Landscape Archaeology  
Department of History and Archaeology  
University of Cyprus  
2026
