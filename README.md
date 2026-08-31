<img width="1536" height="1024" alt="hpYCR1pw1cfgomDDDw4KlYM92p0-LsB_bXgXQc-sZ90Yq4ZzZw" src="https://github.com/user-attachments/assets/6ccf97ed-dc7a-44ac-a5ae-d17af0de6a4b" />
# Early-Cycle Battery Lifetime Prediction Using a Physics-Inspired Hybrid Ensemble

<p align="center">
  <strong>Early-cycle lithium-ion battery lifetime prediction from degradation information available during the first 50 cycles</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-pre--publication-orange">
  <img src="https://img.shields.io/badge/data-available-brightgreen">
  <img src="https://img.shields.io/badge/code-withheld-lightgrey">
  <img src="https://img.shields.io/badge/validation-LOOCV-blue">
</p>

---

## Overview

This repository accompanies a research study on early-cycle lithium-ion battery lifetime prediction.

The study investigates whether long-term battery cycle life can be predicted using degradation information extracted from the early cycling period, with particular emphasis on the first 50 charge–discharge cycles.

The proposed framework combines physics-inspired degradation information with complementary linear and nonlinear regression learners.

> **Repository status: Pre-publication.**  
> The model implementation is intentionally withheld while the associated manuscript is under preparation and has not yet been submitted for publication.

---

## Research Objective

The primary objective is to estimate the long-term cycle life of lithium-ion batteries using information available during the early stages of battery operation.

The study focuses on three main questions:

1. How informative are early-cycle degradation characteristics for predicting long-term battery lifetime?
2. Can physics-inspired degradation information complement purely data-driven predictors?
3. How does the resulting framework behave under strict cell-wise validation and cross-dataset distribution shifts?

---

## Dataset

The primary experimental dataset consists of 27 Panasonic NCR18650 lithium-ion battery cells evaluated under heterogeneous cycling conditions.

The cells were subjected to different operating conditions, including variations in voltage limits and charge/discharge rates.

### Experimental characteristics

| Property | Value |
|---|---:|
| Battery chemistry | Lithium-ion |
| Cell model | Panasonic NCR18650 |
| Number of cells | 27 |
| Early observation window | 50 cycles |
| End-of-life criterion | 70% of initial discharge capacity |
| Reported cycle-life range | 314–1397 cycles |
| Primary validation | Leave-One-Cell-Out Cross-Validation |

Reported operating ranges include:

- Upper cut-off voltage: 4.0–4.2 V
- Lower cut-off voltage: 2.5–3.2 V
- Charge rate: 0.4–0.6 C
- Discharge rate: 0.8–1.2 C

---

## Feature Engineering

A total of 27 early-cycle features were initially considered.

These features characterize different aspects of early battery degradation, including:

- capacity degradation,
- internal resistance behavior,
- energy and efficiency,
- voltage characteristics,
- operational conditions.


Feature selection was performed to identify informative and stable predictors for battery lifetime estimation.

The final cross-dataset analysis focuses on the following ten early-cycle features:

```text
cap_mean_50
cap_std_50
cap_slope_50
cap_c1
cap_c3
cap_c5
cap_delta_50
cap_ratio_50
fading_mean_50
fading_slope_50
```

Detailed feature descriptions are provided in:

`documentation/feature_definitions.md`

---

## Physics-Inspired Degradation Information

A physics-inspired degradation-rate indicator is derived by linking the early capacity-loss behavior to the end-of-life capacity threshold.

Rather than serving as an exact standalone physical lifetime model, this indicator is incorporated as auxiliary degradation information within the proposed hybrid learning framework.

This design provides an interpretable representation of early degradation while allowing nonlinear machine-learning models to capture additional relationships in the feature space.

---

## Hybrid Learning Framework

The proposed framework combines complementary regression models.

### Ridge Regression

Ridge regression provides a regularized linear branch capable of modeling approximately linear relationships between early-cycle features and battery lifetime.

### Extra Trees Regression

Extra Trees provides a nonlinear branch capable of capturing nonlinear relationships and interactions among degradation-related features.

### Ensemble

The predictions of the two branches are combined using equal weighting:

```text
Final Prediction =
0.5 × Extra Trees Prediction
+
0.5 × Ridge Prediction
```

---

## Validation Strategy

The primary evaluation follows a Leave-One-Cell-Out Cross-Validation (LOOCV) protocol.

For every fold:

1. One complete battery cell is held out.
2. The remaining cells are used for model development.
3. Preprocessing is fitted exclusively on the training cells.
4. The model is trained using the training set.
5. The held-out cell is evaluated as an unseen sample.
6. The process is repeated until every cell has served as the held-out test cell.

This cell-wise protocol is used to reduce information leakage and provide a stricter evaluation of generalization to unseen batteries.

Further details are provided in:

`documentation/validation_protocol.md`

---

## Reported In-Domain Performance

The reported performance of the equal-weight Extra Trees + Ridge ensemble is:

| Metric | Value |
|---|---:|
| R² | **0.879** |
| MAE | **84.9 cycles** |
| RMSE | **112.8 cycles** |
| MAPE | **0.125** |

---

## Observation-Window Analysis

Observation windows ranging from 10 to 100 cycles were investigated.

The results indicate that predictive information increases substantially during the early cycling period and approaches a saturation regime around the 50-cycle observation window.

The 50-cycle window therefore provides a practical balance between prediction quality and the amount of cycling data required before making a lifetime estimate.

---

## Cross-Dataset Analysis

The study additionally investigates distributional differences between the experimental battery dataset and the Severson dataset.

Principal Component Analysis (PCA) is used to visualize the feature-space structure.

To quantitatively assess distributional differences, two-sample Kolmogorov–Smirnov (KS) tests are conducted independently for the ten selected early-cycle features.

False Discovery Rate (FDR) correction is applied to account for multiple comparisons.

The resulting KS statistics range from **0.664 to 1.000**, with all FDR-adjusted p-values below **0.001**, indicating substantial distributional differences between the datasets.

Detailed analysis is documented in:

`documentation/cross_dataset_analysis.md`
<img width="1477" height="618" alt="download" src="https://github.com/user-attachments/assets/c3d3c1ae-54d3-4634-a89b-16a84ebcfc20" />

---

## Repository Contents

```text
data/
    Processed feature datasets

documentation/
    Methodology
    Feature definitions
    Validation protocol
    Cross-dataset analysis
    Reproducibility information

figures/
    Supporting and publication-related figures

results/
    Reported tables and supporting results
```

---

## Data Availability

The processed feature dataset included in this repository is provided for research transparency and reproducibility where redistribution is permitted.

Third-party datasets remain subject to their original licenses and terms of use.

Users should obtain and use third-party source datasets according to the conditions specified by their respective providers.

---

## Code Availability

The complete model implementation is **not included in this pre-publication release**.

The source code will be considered for release after the associated manuscript reaches the appropriate publication stage.

The present repository therefore emphasizes:

- data transparency,
- feature documentation,
- methodological description,
- statistical analysis,
- validation methodology, and
- reproducibility information.

---

## Reproducibility

The repository documents the complete experimental logic required to understand the study, including:

- dataset characteristics,
- early-cycle observation window,
- feature construction,
- feature selection,
- physics-inspired degradation information,
- model families,
- ensemble strategy,
- validation protocol,
- cross-dataset analysis, and
- statistical testing.

The implementation itself is currently withheld.

---

## Citation

Please cite the associated research article once it becomes publicly available.

A `CITATION.cff` file is provided as a placeholder and should be updated with the final bibliographic information before publication.

---

## Status

**Pre-submission / Pre-publication**

| Component | Status |
|---|---|
| Processed dataset | ✓ Available |
| Feature documentation | ✓ Available |
| Methodology | ✓ Available |
| Validation protocol | ✓ Available |
| Cross-dataset analysis | ✓ Available |
| Results summary | ✓ Available |
| Model source code | — Withheld |
| Manuscript | — Under preparation |

---

## Contact

For questions regarding the dataset or research, please contact the corresponding author through the contact information associated with the forthcoming publication.e validation.
