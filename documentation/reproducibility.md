[Reproducibility.md](https://github.com/user-attachments/files/31649063/Reproducibility.md)
# Reproducibility

This repository is a pre-publication research release.

## Publicly Documented

The repository documents:

- dataset characteristics,
- observation window,
- feature categories,
- selected features,
- physics-inspired degradation information,
- model families,
- ensemble strategy,
- validation protocol,
- cross-dataset analysis,
- statistical testing,
- reported performance.

## Currently Withheld

The following components are intentionally not included:

- model source code,
- training scripts,
- private preprocessing implementation,
- restricted raw datasets,
- unpublished implementation details.

## Reproduction Workflow

A future complete reproduction should follow:

```text
Authorized raw data
        ↓
Early-cycle feature extraction
        ↓
Feature preprocessing
        ↓
Feature selection
        ↓
Physics-inspired degradation information
        ↓
Ridge Regression
        +
Extra Trees Regression
        ↓
Equal-weight ensemble
        ↓
LOOCV evaluation
        ↓
Performance analysis
        ↓
Cross-dataset analysis
```

## Future Code Release

The implementation may be released after the associated manuscript reaches the appropriate publication stage.
