# Netflix Content Analysis: Data-Driven Insights for Strategic Decisions

## 📌 Project Overview
This project delivers evidence-based insights into the structural drivers of viewer satisfaction on Netflix. Utilizing a comprehensive dataset of 5,000+ titles (1945–2022) sourced from Kaggle, the study builds quantitative models to determine how content attributes—such as runtime, release year, content type, and age certification—influence IMDb user ratings. 

The ultimate goal is to translate raw performance analytics into actionable intelligence for content acquisition teams, audience targeting, and catalog optimization.

---

## 🛠️ Tools & Technologies Used
* **Statistical Analysis Platform:** IBM SPSS Statistics
* **Frameworks:** Extract, Transform, Load (ETL) Data Pipelines, Segmentation Frameworks
* **Methodologies:** Descriptive Analytics, Pearson Correlation, Multiple Linear Regression, Independent Samples T-Testing, One-Way ANOVA with Post-Hoc Tracking, K-Means Clustering

---

## 🔄 Data Pipeline & Engineering (ETL)
To ensure the analytical validity of inferential testing, a systematic data cleaning and transformation protocol was executed:
* **Missing Data Mitigation:** Addressed a 9% missing rate in dependent variables. Applied listwise deletion for runtime gaps to defend regression model assumptions, and targeted mean imputation for missing IMDb ratings sitting within the safe 5%–20% volatility threshold.
* **Feature Engineering & Categorical Binning:**
    * Transformed continuous temporal records (`release_year`) into **13 discrete decade groupings** to map long-tail engagement trends.
    * Migrated a complex string attribute (`type`) into a binary integer field (`Movies = 1`, `Shows = 2`) utilizing SPSS Automatic Recode workflows to execute parametric t-tests.
    * Consolidated sparse age certifications into **4 high-power demographic bins**: *Children* (G/TV-G/TV-Y), *Family* (PG/PG-13/TV-PG), *Mature* (R/TV-14/TV-MA), and *Restricted/Not Rated* (NC-17/NR) to minimize sampling noise and increase ANOVA statistical power.

---

## 📊 Key Analytical Findings & Business Insights

### 1. Descriptive & Correlation Landscape
* The platform baseline rating across 5,368 valid titles sits at a stable mean of **6.51** ($SD = 1.16$), exhibiting a slight negative skew—proving the library is baseline-anchored around dependable, average-quality inventory.
* **Negative Drivers:** IMDb scores correlated negatively with runtime ($r = -0.148, p < .001$) and release year ($r = -0.129, p < .001$), revealing a baseline pattern where bloated runtimes and newer, mass-produced library assets struggle slightly against leaner historical content.

### 2. Inferential Modeling (Regression, T-Test, & ANOVA)
* **Predictive Limits of Runtime:** Multiple linear regression showed that while runtime is statistically significant ($\beta = -0.148, p < .001$), it accounts for only **2.2% of total rating variance** ($R^2 = 0.022$). Strategic takeaway: Content length should be treated as a secondary metric rather than a primary filter for catalog investments.
* **The Format Advantage:** An Independent Samples T-Test revealed that **TV Shows significantly outperform Movies** ($t(4176.09) = -23.48, p < .001$), averaging **0.73 points higher** on the IMDb metric with a large Cohen's effect size ($d = 0.73$). Movies show wider structural volatility and higher extreme downside outlier counts.
* **Demographic Performance:** One-Way ANOVA mapping ($F(3, 2918) = 29.41, p < .001$) accompanied by Tukey/Games-Howell post-hoc testing proved that **Mature-rated content** (Group 3, Mean = 6.86) structurally outperforms **Restricted/Unrated assets** (Group 4, Mean = 6.15) by a notable gap of **0.71 points** ($p < .001$).

### 3. Advanced Catalog Segmentation (K-Means Clustering)
A 3-cluster K-Means solution successfully segmented the inventory matrix:
* **Cluster 1 (High-End Historical):** High ratings (6.6), extended runtime (136 min), early vintage (2013 centroid baseline).
* **Cluster 2 (Mass Market Current):** Moderate ratings (6.2), medium runtime (95 min), hyper-modern era (2017).
* **Cluster 3 (High-Engagement Lean Content):** Top-tier ratings (6.8), condensed runtimes (40 min), modern serialization era (2017).

---

## 📈 Strategic Strategic Recommendations
1.  **Double-Down on Serialized Formats:** Prioritize TV Show architecture for retention objectives, as continuous formats demonstrate superior structural rating stability and tighter variance than stand-alone features.
2.  **Mitigate Movie Asset Downside Risk:** Implement strict content-quality gates on new movie acquisitions to combat the high-volume downside rating skew identified in exploratory processing.
3.  **Target the Mature Demographic Sweet Spot:** Allocate procurement and development budgets preferentially toward well-scoped Mature-rated serialized productions, which yield the highest audience return metrics.

---
*Note: This analysis was completed as part of the DAT7001 Data Handling and Decision Making module requirements at Arden University.*
