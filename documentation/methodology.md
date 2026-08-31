[Methodology.md](https://github.com/user-attachments/files/31649016/Methodology.md)
# Methodology

## Problem Definition

The objective is to predict long-term lithium-ion battery cycle life using degradation information available during the early cycling period.

Battery end of life is defined at 70% of the initial discharge capacity.

## Early-Cycle Observation

The primary analysis uses the first 50 charge–discharge cycles.

## Feature Engineering

Twenty-seven early-cycle features are initially considered.

The features describe multiple aspects of degradation and operating behavior, including capacity, resistance, energy, efficiency, voltage characteristics, and operating conditions.

## Physics-Inspired Degradation Information

A physics-inspired degradation-rate indicator is derived by relating early capacity-loss behavior to the end-of-life threshold.

The indicator is introduced as auxiliary degradation information within the hybrid framework.

## Machine-Learning Components

### Ridge Regression

Ridge regression models regularized linear relationships between early-cycle features and lifetime.

### Extra Trees Regression

Extra Trees models nonlinear relationships and interactions among predictors.

### Ensemble

The two predictions are combined using equal weighting.

```text
Final Prediction =
0.5 × Ridge Prediction
+
0.5 × Extra Trees Prediction
```

## Validation

LOOCV is used to evaluate generalization to unseen battery cells.

## Cross-Dataset Analysis

PCA and two-sample KS testing are used to investigate distributional differences between datasets.
