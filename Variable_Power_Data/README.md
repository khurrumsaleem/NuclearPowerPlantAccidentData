# Variable-Power Extension of NPPAD

## Overview

This directory contains the variable-power extension of NPPAD. It provides 12 scenarios: four normal power-transition trajectories and eight accident trajectories during power changes. Every scenario uses a ramp-rate demand of **1% rated power per minute**.

## Scenario Design

The normal power trajectories are 80% to 100%, 100% to 80%, 70% to 90%, and 90% to 70%. The accident scenarios cover hot-leg LOCA, rod ejection / rapid rod withdrawal, Steam Generator A Tube Rupture, and Steam Generator B Tube Rupture. Each fault type is represented during both the 80%-to-100% power increase and the 100%-to-80% power decrease.

## Directory Structure

Directory names combine an operating-condition code with the power transition:

- `NORM`: normal operation;
- `LOCA`: hot-leg loss-of-coolant accident;
- `RW`: rod ejection / rapid rod withdrawal;
- `SGATR`: Steam Generator A Tube Rupture;
- `SGBTR`: Steam Generator B Tube Rupture.

For example, `LOCA_80_to_100` contains the hot-leg LOCA scenario during the 80%-to-100% power increase.

## Scenario Table

| Source folder | Scenario directory | Start power | End power | Ramp rate | Fault | Injection time | Failure fraction / setting |
|---|---|---:|---:|---:|---|---:|---|
| N1 | `NORM_80_to_100` | 80% | 100% | 1%/min | None | NA | NA |
| N2 | `NORM_100_to_80` | 100% | 80% | 1%/min | None | NA | NA |
| N3 | `NORM_70_to_90` | 70% | 90% | 1%/min | None | NA | NA |
| N4 | `NORM_90_to_70` | 90% | 70% | 1%/min | None | NA | NA |
| N5 | `LOCA_80_to_100` | 80% | 100% | 1%/min | Hot-leg LOCA | 2298.5 s | 5% of 100 cm² |
| N6 | `RW_80_to_100` | 80% | 100% | 1%/min | Rod Ejection / Rapid Rod Withdrawal | 2296.5 s | 1% (+/-) withdrawn/insertion |
| N7 | `SGATR_80_to_100` | 80% | 100% | 1%/min | Steam Generator A Tube Rupture | 2303 s | 0.2% of one full tube rupture |
| N8 | `SGBTR_80_to_100` | 80% | 100% | 1%/min | Steam Generator B Tube Rupture | 2299.5 s | 0.2% of one full tube rupture |
| N9 | `LOCA_100_to_80` | 100% | 80% | 1%/min | Hot-leg LOCA | 915 s | 5% of 100 cm² |
| N10 | `RW_100_to_80` | 100% | 80% | 1%/min | Rod Ejection / Rapid Rod Withdrawal | 917 s | 1% (+/-) withdrawn/insertion |
| N11 | `SGATR_100_to_80` | 100% | 80% | 1%/min | Steam Generator A Tube Rupture | 905 s | 0.2% of one full tube rupture |
| N12 | `SGBTR_100_to_80` | 100% | 80% | 1%/min | Steam Generator B Tube Rupture | 910 s | 0.2% of one full tube rupture |

The same metadata are available in machine-readable form in [`manifest.csv`](manifest.csv).

## File Organization

Each scenario directory contains the three original simulation artifacts:

```text
case1.mdb
case1.txt
case1dose.mdb
```

The source bytes were not modified; the files were only copied into the scenario-based directory organization. Because the local source files for N2 through N12 were numbered by source folder (`case2.*` through `case12.*`), their target copies use the consistent filenames above. The source and target filenames, sizes, and hashes are recorded in [`file_checksums.csv`](file_checksums.csv).

## Data Integrity

The data were copied directly from the local N1 through N12 directories. SHA-256 checksums were calculated for every source and target file, and all source-target pairs match. No data were resampled, interpolated, smoothed, normalized, or otherwise modified.

## Relationship to Original NPPAD

The existing `NPPAD/` directory remains unchanged. This extension is isolated under `Variable_Power_Data/`, so it does not alter existing data paths or processing workflows.

## Citation and License

Please cite NPPAD as:

> Qi, B., Xiao, X., Liang, J. et al. An open time-series simulated dataset covering various accidents for nuclear power plants. *Scientific Data* 9, 766 (2022). https://doi.org/10.1038/s41597-022-01879-1

This extension follows the repository's [MIT License](../LICENSE).
