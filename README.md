# A GIS Framework for Risk Management of Immovable Cultural Heritage in Northern Thrace

This repository contains the supporting material for the master's thesis *A GIS Framework for Risk Management of Immovable Cultural Heritage: A Case Study in Northern Thrace (Southern Bulgaria)*.

The study develops a GIS-based regional framework for assessing relative archaeological risk by integrating seismic hazard, flooding, wildfire, landslide susceptibility, soil erosion, and archaeological site vulnerability. Archaeological sites are grouped according to similar environmental conditions before cluster-specific Analytic Hierarchy Process (AHP) weighting is applied. The resulting weights are combined with standardized risk criteria using weighted linear combination (WLC). The framework is further evaluated using Getis-Ord Gi* hot spot analysis, One-at-a-Time (OAT) sensitivity analysis, and Monte Carlo uncertainty analysis.

## Repository contents

The repository contains supporting material used in the analytical workflow, including:

- environmental and spatial data or supporting data-access information;
- archaeological site data prepared for analysis;
- environmental clustering scripts, input data, results, and visualizations;
- cluster-specific AHP pairwise comparison matrices and calculations;
- analytical data used in the weighted archaeological risk assessment;
- OAT sensitivity-analysis scripts and results;
- Monte Carlo uncertainty-analysis scripts and results; and
- supporting documentation for reproducing and interpreting the analyses.

Individual analytical folders contain their own README files with more detailed descriptions of the methods, inputs, outputs, dependencies, and file structure.

## Analytical workflow

The main analytical components are:

1. Environmental and archaeological data preparation
2. Environmental spatial clustering
3. Cluster-specific Analytic Hierarchy Process (AHP)
4. Weighted Linear Combination (WLC)
5. Getis-Ord Gi* hot spot analysis
6. OAT sensitivity analysis
7. Monte Carlo uncertainty analysis

## Repository structure

```text
Thesis_Risk_Assessment_Data_Northern_Thrace/
├── README.md
├── clustering/
│   └── ...
├── environmental_data/
│   └── ...
├── site_data/
│   └── ...
├── ahp/
│   └── ...
├── sensitivity/
│   └── ...
└── monte_carlo/
    └── ...
