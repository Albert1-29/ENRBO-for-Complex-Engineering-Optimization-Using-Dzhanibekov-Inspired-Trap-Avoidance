# An Enhanced Newton-Raphson-Based Optimizer for Complex Engineering Optimization Using Dzhanibekov-Inspired Trap Avoidance

Experimental results for the ENRBO manuscript by Ziting Zhao and Hui Wang.
The six numbered sections retain the original project directory names,
experiment subdirectories and result-file locations. This repository contains
results only. MATLAB `.m` source files are excluded throughout, including
historical source-snapshot directories.

## Results by experiment

| Directory | Contents | Result files |
|---|---|---:|
| [0_Hypothesis_Validation](0_Hypothesis_Validation) | Initialization, NRSR, TAO, decay, DE and complete-version development comparisons | 3,523 |
| [1_Parameter_Sensitivity_Analysis](1_Parameter_Sensitivity_Analysis) | DF sensitivity results | 718 |
| [2_Comparative_Experiments](2_Comparative_Experiments) | CEC2017 and CEC2022 comparisons | 750 |
| [3_Ablation_Study](3_Ablation_Study) | NRBO and independent single-strategy additions | 611 |
| [4_Qualitative_Analysis](4_Qualitative_Analysis) | Classical-function trajectory records and figures | 612 |
| [5_Application_Experiments](5_Application_Experiments) | Constrained engineering and grid-map path planning | 51,138 |

The archive contains 57,352 original non-`.m` result files, totaling
3,849,715,417 bytes. It includes original Excel and CSV
tables, MAT records, and saved FIG, PDF and PNG figures. Each run directory keeps
its original name. Results stored directly in the initialization study's
dimension folders remain in those locations.

## Records used for the final evaluation

- **DF sensitivity:** `1_Parameter_Sensitivity_Analysis/Results/run_20261028_090507_233`.
- **CEC comparisons:** the `Results` folders in `2_Comparative_Experiments/CEC2017`
  and `2_Comparative_Experiments/CEC2022`.
- **Independent additions:** `3_Ablation_Study/Results`.
- **Final-ENRBO qualitative runs:** `4_Qualitative_Analysis/Results/run_20261027_164808_291`.
- **57 engineering problems:** `5_Application_Experiments/0_2020_RW_Constrained_Optimisation/Results/Run_20261028_073128_834`.
- **50 final grid maps:** `5_Application_Experiments/1_Path_Planning/Results/Validation50_Uniform_20261030_205554_362`.

Earlier saved runs remain in their original directories as development records.
Version names have the meaning assigned in each experiment. In particular,
the initialization A1/A2 labels refer to initialization alternatives; the
NRSR study uses those labels for different search-rule versions.

Original numerical CSV files retain their saved display precision. The raw MAT
arrays preserve the full stored floating-point values, run seeds and other
recorded fields. Use these arrays when reproducing statistics involving ties.
The qualitative results are single illustrative runs. The path tables' zero,
one and two smoothing passes are three states of the same optimization runs.
Each result folder supplies its own protocol and metadata where recorded.

## Downloading the complete dataset

Three aggregate MAT files use Git Large File Storage (Git LFS) at their original
paths. Install Git LFS, clone this repository, then run:

```text
git lfs pull
```

Excel, CSV, PDF and PNG files can also be opened or downloaded individually in
the experiment folders. MATLAB opens FIG files and reads MAT records. Aggregate
MAT files are accompanied by the originally saved per-run records and tables.

`RESULTS_MANIFEST.csv` lists the original relative paths, sizes and SHA-256
checksums. Empty result directories use `.gitkeep` to retain their locations.
The two original zero-byte `RUNNING.lock` files are retained as archived status
markers. Preparing this repository copied existing results and did not run
optimization or change the source experiment projects.

The benchmark materials and notices retained in result snapshots remain subject
to their original terms.
