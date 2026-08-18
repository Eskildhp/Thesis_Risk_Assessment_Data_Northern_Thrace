# Public Site Dataset

This folder contains the sanitized public version of the archaeological site master table used in the Northern Thrace risk assessment.

The table brings together the archaeological, descriptive, environmental, and analytical attributes used throughout the thesis workflow.

## File

`Sites_master.csv`

The file contains 250 archaeological sites included in the final analysis.

## Contents

The dataset includes fields relating to:

* site identification and naming
* municipality and administrative context
* chronological periods and site types
* material and physical characteristics
* exposure and asset vulnerability
* environmental variables
* standardized hazard and vulnerability scores
* environmental cluster assignment
* final WLC risk score and risk class
* selected analytical outputs used in later stages of the thesis

The exact field names follow the working database used during the analysis.

## Archaeological information

The archaeological attributes include the site name and identifier together with descriptive information such as chronology, site type, material, exposure, and other characteristics used to evaluate Asset Vulnerability.

Some fields contain period-specific classifications because a site may have different functions or archaeological characteristics during different chronological phases.

## Environmental and risk fields

The dataset also contains the environmental variables and standardized criterion scores used in the risk model.

The standardized risk fields include:

|Field|Description|
|-|-|
|`SEIS_SCR`|Standardized seismic hazard score|
|`FLOOD_SCR`|Standardized flood hazard score|
|`FWI_SCR`|Standardized wildfire hazard score|
|`ELSUS_SCR`|Standardized landslide susceptibility score|
|`RUSLE_SCR`|Standardized soil erosion score|
|`ASSET_SCR`|Standardized asset vulnerability score|
|`Cluster_3`|Environmental cluster assigned during Ward hierarchical clustering|
|`WLC_RISK`|Final cluster-weighted WLC risk score|
|`RISK_CLASS`|Final categorical risk classification|

Additional environmental fields preserve supporting values and method/status information used during data preparation.

## Method/status fields

Several fields ending in `_MTH` record how values were assigned, corrected, excluded, or treated during the analysis.

For example:

|Field|Description|
|-|-|
|`Rusle_MTH`|Method/status information for the RUSLE soil-erosion criterion|
|`ELSUS_MTH`|Method/status information for the ELSUS landslide-susceptibility criterion|

These fields are retained because they document intentional exclusions and NoData handling used in the sensitivity and uncertainty analyses.

## Field descriptions

The following fields provide additional archaeological and analytical information used in the thesis database.

|Field|Description|
|-|-|
|`Site_ID`|Unique identifier assigned to each archaeological site|
|`Site`|Standardized archaeological site name|
|`Municipality`|Municipality in which the site is located|
|`Material_general`|Generalized construction material or physical composition of the site|
|`Exposure`|General classification of the site's physical exposure|
|`Cluster_3`|Final environmental cluster used for the cluster-specific AHP model|

## Data sanitization

This public dataset is derived from the final internal site master table but excludes precise archaeological site coordinates.

The following spatial fields are not included:

* `X_coordinate`
* `Y_coordinate`

The public table therefore preserves the archaeological and analytical attributes needed to understand and reproduce the thesis workflow without publishing precise site locations.

The final WLC fields are presented under the simplified names:

* `WLC_RISK`
* `RISK_CLASS`

Earlier superseded WLC and risk-class fields are not included.

## Relationship to the repository

`Sites_master.csv` is the central public site-level dataset for the repository.

More specialized sanitized input files are provided within the individual analysis folders where required:

* `clustering/` contains the transformed clustering variables
* `risk_assessment/` contains the final site-level WLC results
* `sensitivity_analysis/inputs/` contains the fields required for the OAT sensitivity analysis
* `uncertainty_analysis/inputs/` contains the fields required for the Monte Carlo uncertainty analysis

These specialized files are derived from the same broader site database but are limited to the fields required for each analytical stage.

## Repository structure

    data/
    ├── README.md
    └── Sites_master.csv

## Data use

The dataset is provided as supporting material for the thesis and should be interpreted together with the methodology and data-source documentation in the thesis and repository.

Precise archaeological site coordinates are not included in the public repository.
