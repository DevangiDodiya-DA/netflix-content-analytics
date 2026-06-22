# Data Cleaning & Transformation Log (The "Why" Behind the Choices)

When I first opened the raw Netflix dataset, it was clear that while the data was incredibly rich, it wasn't ready for rigorous parametric testing right out of the box. To make sure my regression models, t-tests, and ANOVAs were actually valid and didn't violate key statistical assumptions, I put the data through a deliberate Extract, Transform, Load (ETL) pipeline in IBM SPSS.

Here is a plain-text breakdown of the issues I found and exactly how I handled them.

---

## 1. Dealing with Missing Data (The Baseline Defense)
The dataset contained a noticeable 9% missing value rate within the `imdb_score` variable. 
* **The Choice:** I used **listwise deletion** for cases missing runtime data because imputing a dependent outcome variable would completely compromise the integrity of my predictive models. 
* **The Imputation:** However, for the independent `imdb_score` missing windows that sat comfortably within the safe 5%–20% threshold, I applied **mean imputation**. This allowed me to preserve a massive, robust sample size ($N = 5,368$) without introducing artificial volatility or ruining data representativeness.

---

## 2. Transforming the Content 'Type' (Text to Numbers)
The platform splits assets into two core types: `MOVIE` and `SHOW`. Unfortunately, SPSS parametric test modules cannot run mathematical comparisons on raw text strings.
* **The Choice:** I used the **Automatic Recode** function in SPSS to map this string attribute into a clean binary integer field where `MOVIE = 1` and `SHOW = 2`. This simple engineering step unblocked my ability to run an Independent Samples T-Test to see which format format structurally commands higher viewer appreciation.

---

## 3. Binning Release Years into Decades (Taming the Timeline)
The data spans nearly eight decades (1945 to 2022). Trying to plot or analyze individual years creates a lot of baseline noise and unhelpful granularity.
* **The Choice:** I executed a structural recode to group individual `release_year` continuous values into **13 discrete decade brackets** (e.g., mapping 1970–1979 as a single cohort). This compressed the long-tail timeline into clean, scannable segments, making macro historical patterns immediately clear to non-technical stakeholders on a trend line graph.

---

## 4. Consolidating Age Certifications (Maximizing Statistical Power)
The raw data for content ratings was incredibly fragmented (G, TV-G, TV-Y, PG, PG-13, TV-PG, R, TV-14, TV-MA, NC-17, NR). Leaving them separated meant some categories had tons of records while others were practically empty. This unequal distribution ruins the structural power of a One-Way ANOVA.
* **The Choice:** I consolidated the sparse cells into **4 high-power demographic bins**:
  1. **Children** (G, TV-G, TV-Y)
  2. **Family** (PG, PG-13, TV-PG)
  3. **Mature** (R, TV-14, TV-MA)
  4. **Restricted/Not Rated** (NC-17, NR)
* **The Outcome:** This structural data reduction drastically lowered our variance errors, leveled out group sample distributions, and directly enabled a high-confidence Tukey/Games-Howell post-hoc evaluation.

---

## Summary of Final Analytical Readiness
By systematically treating these data quirks beforehand, the final dataset satisfied the key parametric assumptions:
* **Bivariate Normality** was verified via visual curve histograms (confirming a slight, predictable negative skew centered around a 6.51 mean).
* **Homogeneity of Variance** boundaries were cleanly audited via Levene's testing so I knew exactly when to interpret the "Equal Variances Not Assumed" test constraints.
