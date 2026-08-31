[Cross-Dataset Distribution Analysis.md](https://github.com/user-attachments/files/31648977/Cross-Dataset.Distribution.Analysis.md)
# Cross-Dataset Distribution Analysis

## Objective

The cross-dataset analysis evaluates whether the feature distributions of the primary experimental dataset are consistent with those of the Severson dataset.

This analysis is important for interpreting cross-dataset prediction performance.

## PCA Analysis

Principal Component Analysis (PCA) is used to project the selected early-cycle features into a lower-dimensional representation.

The PCA projection provides a visual assessment of the degree of overlap or separation between the datasets.

## Kolmogorov–Smirnov Test

A two-sample Kolmogorov–Smirnov (KS) test is performed independently for each of the ten selected early-cycle features.

The KS statistic measures the maximum difference between the empirical cumulative distributions of the two datasets.

## Multiple-Testing Correction

False Discovery Rate (FDR) correction is applied to the feature-wise p-values.

All ten evaluated features exhibit statistically significant distributional differences after FDR correction.

The reported KS statistics range from:

```text
0.664 to 1.000
```

and all adjusted p-values are below:

```text
0.001
```

## Interpretation

The results indicate substantial feature-level distributional differences between the two datasets.

These differences provide quantitative evidence of dataset shift and should be considered when interpreting cross-dataset transfer performance.

## Selected Features

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
