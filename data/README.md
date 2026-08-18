# Public Site Dataset

This folder contains the public version of the archaeological site master table containing the descriptive, environmental and analytical attributes used in the thesis workflow.

### File

`Sites\_master.csv`

The file contains 250 archaeological sites included in the final analysis.

### Contents

The dataset includes fields relating to:

* Site identification and naming
* Municipality and administrative context
* Chronological periods and site types
* Material and physical characteristics
* Exposure and asset vulnerability
* Environmental variables
* Standardized hazard and vulnerability scores
* Environmental cluster assignment
* Final WLC risk score and risk class
* Selected analytical outputs 

The exact field names correspond to the working database used in the analysis.

### Archaeological information

The archaeological attributes include the site name and identifier and descriptive information such as chronology, site type, material, exposure and other characteristics used to evaluate Asset Vulnerability.

Some fields contain period-specific classifications because a site may have different functions or archaeological characteristics during different chronological phases.

### Environmental and risk fields

The dataset also contains the environmental variables and standardized criterion scores used in the risk model.

The standardized risk fields include:

|Field|Description|
|-|-|
|`SEIS\_SCR`|Standardized seismic hazard score|
|`FLOOD\_SCR`|Standardized flood hazard score|
|`FWI\_SCR`|Standardized wildfire hazard score|
|`ELSUS\_SCR`|Standardized landslide susceptibility score|
|`RUSLE\_SCR`|Standardized soil erosion score|
|`ASSET\_SCR`|Standardized asset vulnerability score|
|`Cluster\_3`|Environmental cluster assigned during Ward hierarchical clustering|
|`WLC\_RISK`|Final WLC risk score|
|`RISK\_CLASS`|Final risk classification|

Additional environmental fields have supporting values and method/status information used during data preparation.

### Method/status fields

Several fields ending in `\_MTH` record how values were assigned, corrected, excluded or handled during the analysis.

For example:

|Field|Description|
|-|-|
|`Rusle\_MTH`|Method/status information for the RUSLE soil erosion criterion|
|`ELSUS\_MTH`|Method/status information for the ELSUS landslide susceptibility criterion|

These fields document intentional exclusions and NoData handling used in the sensitivity and uncertainty analyses.

### Field descriptions

The following fields provide additional archaeological and analytical information used in the thesis database.

|Field|Description|
|-|-|
|`Site\_ID`|Unique identifier assigned to each archaeological site|
|`Site`|Standardized archaeological site name|
|`Municipality`|Municipality where the site is located|
|`Material\_general`|Construction material or physical composition of the site|
|`Exposure`|General classification of the site's physical exposure|
|`Cluster\_3`|Final environmental cluster used for the cluster-specific AHP model|

### Data sanitization

This public dataset is derived from the final internal site master table but excludes precise archaeological site coordinates.

The following spatial fields are not included:

* `X\_coordinate`
* `Y\_coordinate`

The public table contains the archaeological and analytical attributes needed to understand and reproduce the thesis workflow without publishing precise site locations.

The final WLC fields are presented under the simplified names:

* `WLC\_RISK`
* `RISK\_CLASS`

Earlier WLC and risk-class fields are not included.

### Relationship to the repository

`Sites\_master.csv` is the central public site-level dataset for the repository.

More specialized input files are located in the individual analysis folders where needed:

* `clustering/` contains the transformed clustering variables
* `risk\_assessment/` contains the final WLC results
* `sensitivity\_analysis/inputs/` contains the fields required for the OAT sensitivity analysis
* `uncertainty\_analysis/inputs/` contains the fields required for the Monte Carlo uncertainty analysis

The specialized files are derived from the same site database but are limited to the fields required for each analytical stage.

### Repository structure

&#x20;   data/
    ├── README.md
    └── Sites\_master.csv


### Data use

The dataset is provided as supporting material for the thesis and should be interpreted together with the methodology and data source documentation in the thesis and repository.

Precise archaeological site coordinates are not included in the public repository.

