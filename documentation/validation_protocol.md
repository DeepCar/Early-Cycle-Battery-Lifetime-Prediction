[Validation Protocol.md](https://github.com/user-attachments/files/31648963/Validation.Protocol.md)
# Validation Protocol

## Leave-One-Cell-Out Cross-Validation

The primary evaluation uses Leave-One-Cell-Out Cross-Validation (LOOCV).

Each complete battery cell is treated as an independent evaluation unit.

For each fold:

1. One cell is removed from the dataset.
2. The remaining cells are used for model development.
3. Preprocessing is fitted using only the training cells.
4. Model development is performed using the training data.
5. The held-out cell is evaluated without being used during model development.
6. The process is repeated until every cell has served as the held-out sample.

## Leakage Prevention

All data-dependent preprocessing operations should be performed within the corresponding training fold.

This includes, where applicable:

- imputation,
- normalization or scaling,
- feature selection,
- model fitting,
- hyperparameter selection.

The held-out cell must not influence these operations.

## Evaluation Metrics

The study reports:

- R²
- MAE
- RMSE
- MAPE

MAE and RMSE are expressed in battery cycles.

## Rationale

Cell-wise validation is used because randomly splitting individual observations can result in information leakage when observations from the same physical battery appear in both training and test sets.
