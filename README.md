# Differences-in-general-practitioners-mental-health-diagnosing-and-its-association-with-patient-care
Code connected to Differences in general practitioners' use of mental health diagnosing and its association with patient care: A Norwegian Registry Study Schepers et al.


This repository contains **fully generic, reusable R scripts** for running fixed-effects regressions, instrumental variable (IV) regressions, and spline-based bootstrap analyses using the `fixest` package.  

All variable names are anonymized with placeholders, so these scripts are safe to publish publicly. Users can easily replace placeholders with their own dataset and variable names.  

---

## Table of Contents

1. [Overview](#overview)  
2. [Scripts](#scripts)  
3. [Setup](#setup)  
4. [Usage](#usage)  
5. [Notes](#notes)  
6. [License](#license)  

---

## Overview

These scripts cover three main types of analyses:

1. **Standard Fixed-Effects Regression (`feols`)**  
   - Run linear regressions with arbitrary covariates, fixed effects, and cluster-robust standard errors.  
   - Fully parameterized to allow any outcome variable, treatment, and subset of the data.  

2. **Instrumental Variable (IV) / Two-Stage Fixed-Effects Regression (`feols`)**  
   - Run IV regressions with user-defined endogenous variables, instruments, covariates, fixed effects, and clustering.  
   - Can be applied to any dataset subset.  

3. **Spline-Based Bootstrap Analysis**  
   - Estimates partial effects of one or more continuous variables using natural cubic splines.  
   - Bootstraps the effect to generate **median effects and 95% confidence intervals**.  
   - Fully generic to allow any outcome, instrument, covariates, and subset.  
   - Produces publication-ready plots using `ggplot2`.  

---

## Scripts

| Script Name | Description |
|------------|-------------|
| `generic_feols.R` | Standard fixed-effects regression template. Placeholder variables for outcome, treatment, covariates, FE, cluster, and subset. |
| `generic_iv_feols.R` | Instrumental variable regression template with placeholders for endogenous variable, instrument, covariates, FE, cluster, and subset. |
| `generic_spline_bootstrap.R` | Bootstrap spline analysis template for continuous instruments. Produces plots with median and 95% CI. Fully parameterized with placeholders. |

---

## Setup

### 1. Install required packages

```r
install.packages(c("fixest", "dplyr", "ggplot2", "splines"))
```
## Usage

| Placeholder                      | Description                                           |
| -------------------------------- | ----------------------------------------------------- |
| `OUTCOME_VAR`                    | The dependent variable in your regression.            |
| `TREATMENT_VAR`                  | The independent or treatment variable of interest.    |
| `ENDOG_VAR`                      | The endogenous variable in IV regressions.            |
| `INSTRUMENT_VAR`                 | Instrument for the endogenous variable.               |
| `COVARIATE_1`, `COVARIATE_2` ... | Any numeric or categorical covariates.                |
| `FE_1`, `FE_2` ...               | Fixed effect variables.                               |
| `CLUSTER_1`, `CLUSTER_2` ...     | Cluster variables for robust standard errors.         |
| `SUBSET_CONDITION`               | Logical condition to subset the data, e.g., `t == 0`. |

## Notes

- All scripts are fully generic: no real variable names appear.
- Can be applied to any dataset with numeric or categorical variables.
- Bootstrap spline script can profile multiple instruments simultaneously.
- Cluster-robust standard errors are supported in all scripts.


