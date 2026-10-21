# WeatherIndex

WeatherIndex contains the code and weather-data snapshot for a master's research project completed at Delft University of Technology (TU Delft) in 2024. It explores clustering hourly weather observations and deriving a heuristic weather-severity index in the context of AIS-based ship arrival-time research for inland waterway transport.

The work was conducted entirely within TU Delft, without an external commissioning organisation. The code was published at the university supervisor's request. It is retained as an academic portfolio and research reference, rather than an actively maintained application.

Project author: Erik Le Blansch (2024). Reference snapshot: [WeatherIndex at commit `6e6102f97353fc882d8b0f1d7b0ea9a7dcc75e20`](https://github.com/erikleblansch/WeatherIndex/tree/6e6102f97353fc882d8b0f1d7b0ea9a7dcc75e20).

## Data source

**Source: KNMI (Royal Netherlands Meteorological Institute).** The files identify KNMI as their source and contain hourly observations for station 344 (Rotterdam); see [KNMI hourly observations](https://www.knmi.nl/nederland-nu/klimatologie/uurgegevens). The source files are retained in `KNMI_Data.zip`.

The cleaned CSV and clustering results are project transformations, not official KNMI products. No KNMI endorsement is implied. Preserve the source headers and attribution, and identify modifications when sharing derived data. KNMI's [copyright notice](https://www.knmi.nl/copyright) describes its website material as CC0 unless otherwise indicated; check any dataset-specific conditions as well. This README does not assign a new licence to the archived data or the software.

## Files and analysis

- `clustering_analysis.py` — interactive preparation, clustering, summary, and plotting script.
- `KNMI_Data.zip` — raw hourly text files; extract these files into `Data_KNMI/` for the raw-data workflow.
- `KNMI_data_cleaned.zip` — archive containing the prepared `KNMI_data.csv` intermediate.
- `weather_clusters.csv` — example clustering output.

The script compares KMeans, DBSCAN, agglomerative clustering, and Gaussian mixture models using silhouette scores. It then ranks clusters using selected weather extremes to create a heuristic “Weather Index”; the ranking is an exploratory project output, not a validated arrival-time prediction result.

## Running the script

The script requires Python 3 and `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`, and `umap-learn`. Dependency versions and the original environment are not recorded, so exact numerical reproduction with current packages is not guaranteed.

1. Work in a separate copy to preserve the committed research outputs.
2. Extract the raw `.txt` files from `KNMI_Data.zip` directly into a folder named `Data_KNMI/` inside that copy.
3. Set all three `main_path = '<MAIN_PATH>'` assignments in `clustering_analysis.py` to the absolute path of your working copy.
4. Run `python clustering_analysis.py` in an environment with the dependencies above and interactive plotting support. The script processes the raw data before running the clustering stages.
5. Read the nearest-neighbour distance plot and answer the DBSCAN `eps` prompt. The original README records `2.75` for the supplied data; it is a historical parameter, not a general recommendation.

The script writes or overwrites `KNMI_data.csv` and `weather_clusters.csv` and displays plots interactively. The archived `KNMI_data.csv` is available for inspection, but extracting it alone does not bypass the script's raw-data stage. Re-running clustering on the complete dataset can require substantial memory and time. These instructions describe the preserved script; they are not a new reproduction of the research results.

## Academic status and reuse

The associated research report is not included. This snapshot contains weather clustering and derived indices; it does not include an AIS dataset or an arrival-time prediction model. When referencing it, credit the author, cite this repository and record the exact revision used.

No software licence is declared. Public availability on GitHub does not itself grant general permission to reuse the project code. Source-data reuse is governed separately by KNMI's applicable terms. A software licence should only be added after the relevant rights and permissions have been established.
