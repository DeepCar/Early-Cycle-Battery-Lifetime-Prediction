[Feature Definitions.md](https://github.com/user-attachments/files/31648931/Feature.Definitions.md)
# Feature Definitions

The study initially considers 27 early-cycle features.

The features characterize multiple aspects of early battery degradation and operating behavior.

## Final Selected Features

| Feature | Description |
|---|---|
| `cap_mean_50` | Mean capacity-related indicator over the first 50 cycles |
| `cap_std_50` | Standard deviation of the capacity-related indicator |
| `cap_slope_50` | Early-cycle capacity degradation slope |
| `cap_c1` | Capacity-related value at cycle 1 |
| `cap_c3` | Capacity-related value at cycle 3 |
| `cap_c5` | Capacity-related value at cycle 5 |
| `cap_delta_50` | Capacity change over the first 50 cycles |
| `cap_ratio_50` | Capacity ratio associated with the 50-cycle window |
| `fading_mean_50` | Mean early-cycle fading indicator |
| `fading_slope_50` | Early-cycle fading-rate slope |

## Feature Categories

### Capacity

```text
cap_mean_50
cap_std_50
cap_slope_50
cap_delta_50
cap_ratio_50
```

### Resistance

```text
ir_mean_50
ir_slope_50
step_dcir_mean_50
step_dcir_std_50
```

### Energy and Efficiency

```text
engy_mean_50
engy_slope_50
eff_mean_50
eff_drop_50
```

### Voltage

```text
chg_midv_mean_50
chg_midv_slope_50
dchg_midv_mean_50
dchg_midv_slope_50
```

### Operational Parameters

```text
V_high
V_low
C_charge
C_discharge
```

Exact computational definitions should be interpreted consistently with the preprocessing procedure described in the associated manuscript.
