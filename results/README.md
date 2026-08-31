[Results.md](https://github.com/user-attachments/files/31649076/Results.md)
# Results

This directory contains supporting tables and figures associated with the study.

## In-Domain Performance

The reported performance of the equal-weight Extra Trees + Ridge ensemble is:

| Metric | Value |
|---|---:|
| R² | 0.879 |
| MAE | 84.9 cycles |
| RMSE | 112.8 cycles |
| MAPE | 0.125 |

## Cross-Dataset Analysis

The study additionally evaluates transferability between the primary experimental dataset and the Severson dataset.

The observed distributional differences are documented in:

`documentation/cross_dataset_analysis.md`

## Supporting Materials

Recommended files for this directory include:

```text
results/
├── tables/
│   ├── ks_test_results.csv
│   ├── feature_statistics.csv
│   └── performance_summary.csv
│
└── figures/
    ├── PCA_cross_dataset.png
    ├── cross_dataset_boxplots.png
    └── observation_window_analysis.png
```
