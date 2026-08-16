# Environmental Ward Hierarchical Clustering

This folder contains the Python workflow and related data used to group the archaeological sites according to similarities in their environmental characteristics. The analysis uses Ward hierarchical clustering and Euclidean distance. Other solutions of 3-7 clusters are compared using the silhouette scores. The solution with the highest silhouette score is automatically identified and exported with the profiles of the resulting clusters.

## Folder structure

```text
clustering/
├── README.md
├── ward\_clustering\_ruslog.py
├── Cluster\_matrix\_Ruslog.csv
└── results/
    ├── best\_cluster\_profiles.csv
    ├── best\_silhouette\_clusters.csv
    ├── candidate\_cluster\_profiles.csv
    ├── cluster\_evaluation.csv
    ├── sites\_with\_candidate\_clusters.csv
    ├── ward\_dendrogram\_full.png
    └── ward\_dendrogram\_truncated.png
```

An additional `visualization/` folder has contains the script and outputs used to show the environmental characteristics of the final clusters.

## Input data

The clustering script reads:

```text
Cluster\_matrix\_Ruslog.csv
```

The table contains the site identifier, site name and environmental variables for the clustering analysis.

The final clustering model uses the following fields:

|Field|Description|
|-|-|
|`C\_DEM`|Standardized/scaled elevation variable|
|`C\_Slope`|Standardized/scaled slope variable|
|`C\_Acos`|North–south aspect component|
|`C\_Asin`|East–west aspect component|
|`C\_RusLog`|Log-transformed estimated soil-loss variable|
|`C\_FlDist`|Standardized/scaled distance to the modelled flood zone|
|`C\_x`|Transformed spatial x variable used in clustering|
|`C\_y`|Transformed spatial y variable used in clustering|

The final model uses the log-transformed RUSLE variable rather than the original RUSLE values. Distance to the modelled flood zone is maintained. Flood depth is excluded from the final clustering model.

### Spatial data note

`C\_x` and `C\_y` are transformed spatial variables used to introduce a spatial component into the clustering analysis. They are not raw archaeological site coordinates. Raw x/y coordinates of archaeological sites are not included in the public repository.

## Data validation

Before clustering is performed, the script checks that:

* all required fields are present;
* site IDs are not missing;
* site IDs are not duplicated;
* the environmental variables can be interpreted as numeric values; and
* the environmental variables contain no missing values.

The analysis stops if these requirements are not met.

## Clustering procedure

The analysis follows the following main steps:

1. Read the clustering matrix.
2. Validate the required site and environmental data.
3. Extract the eight variables used in the final model.
4. Perform Ward hierarchical clustering using Euclidean distance.
5. Produce full and truncated dendrograms.
6. Generate candidate solutions containing 3, 4, 5, 6, and 7 clusters.
7. Calculate the silhouette score for each candidate solution.
8. Record the size of the smallest, largest and mean cluster for each solution.
9. Add all candidate cluster assignments to the site table.
10. Calculate the mean environmental profile of each cluster.
11. Select the solution with the highest silhouette score.
12. Export the results to the `results/` folder.

## Cluster solution evaluation

The script tests:

```text
3
4
5
6
7
```

clusters.

For each cluster solution, `cluster\_evaluation.csv` records:

* `Requested\_k`
* `Actual\_clusters`
* `Silhouette\_score`
* `Smallest\_cluster`
* `Largest\_cluster`
* `Mean\_cluster\_size`

The evaluation table is sorted from the highest to the lowest silhouette score. The first row is therefore used to identify the preferred cluster solution.

## Outputs

### `cluster\_evaluation.csv`

Summary of the silhouette score and cluster-size statistics for every tested cluster solution.

### `sites\_with\_candidate\_clusters.csv`

Site-level table containing the clustering variables and assignments for all tested solutions:

```text
Cluster\_3
Cluster\_4
Cluster\_5
Cluster\_6
Cluster\_7
```

### `candidate\_cluster\_profiles.csv`

Mean environmental profile and number of sites for each cluster in every tested cluster solution.

### `best\_silhouette\_clusters.csv`

Site identifiers, site names, and cluster assignments for the candidate solution with the highest silhouette score.

The selected assignment is stored as:

```text
Cluster\_best\_silhouette
```

### `best\_cluster\_profiles.csv`

Mean environmental characteristics and number of sites for the clusters belonging to the highest-silhouette solution.

### `ward\_dendrogram\_full.png`

Full Ward hierarchical clustering dendrogram showing the overall hierarchical structure.

### `ward\_dendrogram\_truncated.png`

Truncated dendrogram showing the final 20 merged groups of the hierarchy.

## Running the script

The Python script and input CSV should remain in the same `clustering/` folder.

From a terminal opened in this folder, run:

```bash
python ward\_clustering\_ruslog.py
```

The script automatically identifies its own folder and creates the `results/` directory if it does not already exist.

## Python dependencies

The script uses:

* Python `pathlib`
* NumPy
* pandas
* Matplotlib
* SciPy
* scikit-learn

The external packages can be installed using:

```bash
pip install numpy pandas matplotlib scipy scikit-learn
```
## Software documentation

The Python workflow used the Python standard library and the official NumPy, Pandas, Matplotlib, SciPy and scikit-learn packages. The documentation listed below was used as reference when developing the script.

| Package          | Functionality used in the script                     | Use in this analysis                                                                                                                     | Official documentation                                                                                                                                                                                                      |
| ---------------- | ---------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Python `pathlib` | `Path`, `resolve()`, `parent`, `exists()`, `mkdir()` | Defines file locations for the Python script, checks that the input file exists, and creates the results folder.                 | [Python pathlib documentation](https://docs.python.org/3/library/pathlib.html)                                                                                                                                              |
| pandas           | `read_csv()` and `DataFrame.to_csv()`                | Reads the clustering input matrix and exports the tables as CSV files.                                                         | [pandas I/O documentation](https://pandas.pydata.org/docs/user_guide/io.html)                                                                                                                                               |
| pandas           | `DataFrame.groupby()`                                | Groups archaeological sites according to their assigned cluster so that cluster sizes and mean environmental profiles can be calculated. | [pandas DataFrame.groupby documentation](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.groupby.html)                                                                                                        |
| pandas           | `DataFrame.merge()`                                  | Combines the number of sites in each cluster with the calculated mean environmental profiles.                                            | [pandas merge documentation](https://pandas.pydata.org/docs/reference/api/pandas.merge.html)                                                                                                                                |
| pandas           | `concat()`                                           | Combines the environmental profile tables produced for the different cluster solutions.                                        | [pandas concat documentation](https://pandas.pydata.org/docs/reference/api/pandas.concat.html)                                                                                                                              |
| NumPy            | `unique()`                                           | Counts the number of unique cluster labels returned for each tested cluster solution.                                                    | [NumPy unique documentation](https://numpy.org/doc/stable/reference/generated/numpy.unique.html)                                                                                                                            |
| SciPy            | `scipy.cluster.hierarchy.linkage()`                  | Performs hierarchical agglomerative clustering using Ward's method and Euclidean distance.                                               | [SciPy linkage documentation](https://docs.scipy.org/doc/scipy/reference/generated/scipy.cluster.hierarchy.linkage.html)                                                                                                    |
| SciPy            | `scipy.cluster.hierarchy.fcluster()`                 | Converts the hierarchical clustering into separate cluster solutions containing 3-7 clusters.                                          | [SciPy fcluster documentation](https://docs.scipy.org/doc/scipy/reference/generated/scipy.cluster.hierarchy.fcluster.html)                                                                                                  |
| SciPy            | `scipy.cluster.hierarchy.dendrogram()`               | Produces the full and truncated dendrograms from the hierarchical clustering result.                                                     | [SciPy dendrogram documentation](https://docs.scipy.org/doc/scipy/reference/generated/scipy.cluster.hierarchy.dendrogram.html)                                                                                              |
| scikit-learn     | `sklearn.metrics.silhouette_score()`                 | Calculates the mean silhouette coefficient for each cluster solution so the alternatives can be compared.                      | [scikit-learn silhouette_score documentation](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.silhouette_score.html)                                                                                      |
| Matplotlib       | `pyplot.figure()` and `pyplot.savefig()`             | Creates the dendrogram figures and exports them as PNG files.                                                                            | [Matplotlib figure documentation](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.figure.html) and [Matplotlib savefig documentation](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.savefig.html) |

These sources describe the software implementation of the workflow. The academic support for Ward hierarchical clustering, Euclidean distance and silhouette analysis is listed under methodological references.

## Methodological references

The clustering methodology and evaluation of alternative cluster solutions are based on the following sources:

* Ward, J. H., Jr. (1963). Hierarchical grouping to optimize an objective function. *Journal of the American Statistical Association, 58*(301), 236-244. https://doi.org/10.1080/01621459.1963.10500845

* Rousseeuw, P. J. (1987). Silhouettes: A graphical aid to the interpretation and validation of cluster analysis. *Journal of Computational and Applied Mathematics, 20*, 53-65. https://doi.org/10.1016/0377-0427(87)90125-7

Ward (1963) is the basis for the hierarchical grouping procedure. Observations are successively combined into separate groups while minimizing the increase in variation within the clusters at each stage. Rousseeuw (1987) is the support for the silhouette coefficient used here to compare the alternative cluster solutions.

## Reproducibility and data availability

The repository contains the clustering script, transformed clustering variables, cluster solutions, evaluation results, cluster profiles, and  dendrograms. Raw archaeological site coordinates are not included. The spatial variables included in the clustering matrix (`C\_x` and `C\_y`) are transformed analytical variables rather than raw geographic coordinates.

The files in `results/` are outputs generated from the clustering workflow and are included to make the analytical results directly inspectable without requiring the script to be rerun.
