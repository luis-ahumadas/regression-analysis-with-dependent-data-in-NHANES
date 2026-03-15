# NHANES Diastolic Blood Pressure Analysis

This repository contains a Jupyter Notebook focused on the statistical analysis of **Diastolic Blood Pressure (DBP)** using the 2015-2016 National Health and Nutrition Examination Survey (NHANES) dataset. The project explores the complexities of analyzing dependent data by accounting for survey design variables, such as stratification and clustering.

---

## Project Overview

The primary goal of this analysis is to model blood pressure while accounting for the geographic and demographic "clusters" inherent in the NHANES survey. We utilize **Generalized Estimating Equations (GEE)** and **Multilevel (Mixed-Effects) Models** to assess how much variance in DBP is explained by these clusters versus individual covariates.

### Key Variables

* **Dependent Variable:** `BPXDI1` (Diastolic Blood Pressure).
* **Clustering Variable:** Masked Variance Unit (`MVU`), derived from `SDMVSTRA` (Stratum) and `SDMVPSU` (Primary Sampling Unit).
* **Covariates:** Age (`RIDAGEYR`), Gender (`RIAGENDR`), BMI (`BMXBMI`), and Education Level (`DMDEDUC2`).

---

## Analysis Steps

1. **Data Preprocessing:** Filtering NHANES data, handling missing values, and constructing the `MVU` clustering variable.
2. **Intra-class Correlation (ICC) Assessment:** Using intercept-only GEE models to compare the clustering effects on Systolic vs. Diastolic blood pressure.
3. **Marginal Linear Models (GEE):** Modeling DBP with sex, age, and BMI to observe population-averaged effects while accounting for cluster-robust standard errors.
4. **Gender Stratification:** Splitting the dataset to analyze how BMI and age impact males and females differently.
5. **Multilevel Modeling (LMM):** Fitting mixed-effects models with random intercepts for both geographic clusters (`MVU`) and age cohorts to quantify group-level variance.

---

## Key Findings

* **Low Geographic Clustering:** The ICC for geographic clusters (MVU) was found to be approximately 3%, indicating that most variation in blood pressure is due to individual factors rather than regional location.
* **Gender Differences:** BMI has a significantly stronger positive association with DBP in males than in females, and age shows a significant negative association only in the male cohort.
* **Age-Group Consistency:** When using age as a clustering variable, the ICC rose to 10.8%, suggesting that individuals of the same age share more similarities in DBP than those in the same geographic region.

---

## Requirements

To run this notebook, you will need:

* Python 3.x
* `pandas`
* `numpy`
* `statsmodels`
* `matplotlib` / `seaborn`
