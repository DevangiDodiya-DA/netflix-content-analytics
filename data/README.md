# Data Source & Documentation

To maintain repository optimization and adhere to file-size guidelines, the raw dataset used in this analysis is not hosted directly in this folder. Instead, you can download the verified, primary source file directly from Kaggle.

---

## 📂 Dataset Information
* **Dataset Name:** Netflix Movies and TV Shows
* **Source Platform:** Kaggle
* **Primary Curator:** Victor Soeiro
* **Temporal Scope:** 1945 – 2022
* **Geographic Scope:** United States
* **Dataset Dimensions:** 5,000+ rows × 15 columns

🔗 **[Click here to download the official dataset from Kaggle](https://www.kaggle.com/datasets/victorsoeiro/netflix-tv-shows-and-movies)**

---

## 📋 Schema & Core Variables Modeled
The statistical analysis focused heavily on the following variables extracted from the raw data:

| Variable Name | Data Type | Description | Operationalization / ETL Actions |
| :--- | :--- | :--- | :--- |
| `type` | String / Text | Type of content (Movie or TV Show) | Re-encoded into binary integers (`Movie = 1`, `Show = 2`) via SPSS Automatic Recode. |
| `runtime` | Continuous | Total duration of the title in minutes | Evaluated as a primary predictor in regression modeling; filtered via listwise deletion. |
| `release_year` | Continuous | The calendar year the content was released | Segmented into **13 discrete decade brackets** to track long-tail timeline trends. |
| `age_certification` | Categorical | Official content rating (e.g., PG, R, TV-MA) | Consolidated into **4 high-power demographic bins** (Children, Family, Mature, Restricted). |
| `imdb_score` | Continuous | Weighted user rating average on IMDb (0.0–10.0) | Serving as the **Primary Dependent Variable (Y)**; missing entries balanced via mean imputation. |
| `imdb_votes` | Continuous | Total count of user ratings submitted on IMDb | Used to measure audience engagement metrics during the correlation phase. |

---

## ⚖️ Data Attribution & Citation
This analysis relies on secondary public data scraped from the official Netflix database in July 2022. If you use this schema layout or data setup for research, please attribute the original curator:

> Soeiro, V. (2024). *Netflix Movies and TV Shows*. Kaggle Datasets. Available at: https://www.kaggle.com/datasets/victorsoeiro/netflix-tv-shows-and-movies
