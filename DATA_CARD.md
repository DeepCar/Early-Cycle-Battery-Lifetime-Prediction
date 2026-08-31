[Data Card.md](https://github.com/user-attachments/files/31648793/Data.Card.md)
# Data Card

## Dataset

Early-cycle lithium-ion battery degradation features for battery lifetime prediction.

## Purpose

The dataset is intended to support research into early prediction of long-term lithium-ion battery cycle life.

## Primary Dataset

- Battery type: Lithium-ion
- Cell model: Panasonic NCR18650
- Number of cells: 27
- Early-cycle observation window: 50 cycles
- End-of-life criterion: 70% of initial discharge capacity

## Operating Conditions

Reported operating ranges include:

| Parameter | Range |
|---|---:|
| Upper cut-off voltage | 4.0–4.2 V |
| Lower cut-off voltage | 2.5–3.2 V |
| Charge rate | 0.4–0.6 C |
| Discharge rate | 0.8–1.2 C |

## Feature Development

Twenty-seven early-cycle features were initially considered.

The final cross-dataset analysis uses ten selected features:

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

## Intended Use

The data are intended for:

- battery degradation research,
- battery lifetime prediction,
- feature analysis,
- distribution-shift analysis,
- machine-learning benchmarking,
- reproducibility studies.

## Limitations

The dataset has several important limitations:

- relatively small number of primary experimental cells,
- limited cell-model diversity,
- limited chemistry coverage,
- heterogeneous but finite cycling conditions,
- potential cross-dataset distribution shift.

Therefore, results should not automatically be generalized to all lithium-ion batteries or operating environments.

## Third-Party Data

Third-party datasets remain subject to their original licenses, attribution requirements, and redistribution restrictions.

Users are responsible for verifying the applicable terms before redistribution or commercial use.
