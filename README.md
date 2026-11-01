# An Enhanced Newton-Raphson-Based Optimizer for Complex Engineering Optimization Using Dzhanibekov-Inspired Trap Avoidance

Public experimental results for the ENRBO manuscript by Ziting Zhao and Hui Wang.
The archive contains **57,352 original result files (3.85 GB)** across the six numbered sections below. Folder names, run identifiers and result-file locations follow the original project. MATLAB `.m` source files are excluded; this repository is the numerical and figure archive.

## Where to start

1. **Read the results:** choose a study below and open its summary workbook or CSV. Excel files can be downloaded individually.
2. **Inspect one problem:** open its dimension folder, engineering problem rows or map folder. View the corresponding PDF/PNG figures where available.
3. **Check one run:** use the run index and algorithm name to locate its raw MAT record. Protocol and manifest files describe the settings and algorithm order; raw run records retain the seeds.

| Part | Question addressed | First result to open |
|---|---|---|
| [0 Hypothesis validation](0_Hypothesis_Validation) | How did the initialization, NRSR, TAO, decay and DE versions compare during development? | [Development panels](0_Hypothesis_Validation); use the stage summaries listed below |
| [1 Parameter sensitivity](1_Parameter_Sensitivity_Analysis) | How does the branch probability DF affect performance? | [Summary.xlsx](1_Parameter_Sensitivity_Analysis/Results/run_20261028_090507_233/Summary.xlsx) / [Sensitivity figure](1_Parameter_Sensitivity_Analysis/Results/run_20261028_090507_233/DF_Sensitivity_RankCurves.pdf) |
| [2 Comparative experiments](2_Comparative_Experiments) | How does final ENRBO compare with the other optimizers? | [CEC2017 results](2_Comparative_Experiments/CEC2017/Results) / [CEC2022 results](2_Comparative_Experiments/CEC2022/Results) |
| [3 Single-strategy contributions](3_Ablation_Study) | What does each individual strategy contribute when added to NRBO? | [Cross-dimension summary](3_Ablation_Study/Results/CEC2017_WinTieLoss_Summary.xlsx) |
| [4 Qualitative analysis](4_Qualitative_Analysis) | What do the recorded search trajectories and population indicators show? | [46-run summary](4_Qualitative_Analysis/Results/run_20261027_164808_291/Summary.csv) / [F1 figures and history](4_Qualitative_Analysis/Results/run_20261027_164808_291/F1_D30) |
| [5 Application experiments](5_Application_Experiments) | How do the methods perform on constrained engineering and grid-map tasks? | [57-problem workbook](5_Application_Experiments/0_2020_RW_Constrained_Optimisation/Results/Run_20261028_073128_834/Official57_Results.xlsx) / [50-map workbook](5_Application_Experiments/1_Path_Planning/Results/Validation50_Uniform_20261030_205554_362/Results.xlsx) |

For exact file lookup, download [RESULTS_MANIFEST.csv](RESULTS_MANIFEST.csv) and filter the `RelativePath` column. It lists every original result file, its byte size and SHA-256 checksum. The file dictionaries below explain the recurring names and fields.

## Directory map

```text
0_Hypothesis_Validation/
  0_Initialization/D10, D30, D50, D100/
  1_Adaptive_NRSR/Results/
  2_TAO/Results/
  3_delta/Results/
  4_DE/Results/
  5_FINAL/Results/
1_Parameter_Sensitivity_Analysis/
  Results/run_20261028_090507_233/
2_Comparative_Experiments/
  CEC2017/Results/
  CEC2022/Results/
3_Ablation_Study/
  Results/
4_Qualitative_Analysis/
  Results/run_20261027_164808_291/
  Results/run_20261027_105706_988/
5_Application_Experiments/
  0_2020_RW_Constrained_Optimisation/
    Results/Run_20261028_073128_834/
  1_Path_Planning/
    Results/Validation50_Uniform_20261030_205554_362/
    Results/Run_20261030_153005_472/
    Results/Export_Check/
```

`D10`, for example, means a ten-dimensional decision space. A timestamped run folder identifies a saved execution. The links in this guide select the records used for the final evaluation; other saved executions remain in their original locations.

## 0 Hypothesis validation

Each stage has its own version labels and statistical target. For stages 1 to 5, start with the cross-dimension summary, then enter a `D*` folder for the complete function-level results. The initialization stage has a separate workbook for each dimension.

| Stage | Saved comparison | Entry |
|---|---|---|
| `0_Initialization` | Earlier initialization alternatives, named NRBO, NRBOA1 and NRBOA2 in this panel | Workbooks: [10D](0_Hypothesis_Validation/0_Initialization/D10/cec2017_Results_D10.xlsx) / [30D](0_Hypothesis_Validation/0_Initialization/D30/cec2017_Results_D30.xlsx) / [50D](0_Hypothesis_Validation/0_Initialization/D50/cec2017_Results_D50.xlsx) / [100D](0_Hypothesis_Validation/0_Initialization/D100/cec2017_Results_D100.xlsx) |
| `1_Adaptive_NRSR` | NRBO and search-rule versions NRBOA1, NRBOA2 and NRBOA3; target NRBOA3 | [Summary](0_Hypothesis_Validation/1_Adaptive_NRSR/Results/CEC2017_WinTieLoss_Summary.xlsx) / [All dimensions](0_Hypothesis_Validation/1_Adaptive_NRSR/Results) |
| `2_TAO` | NRBO, NRBOA and TAO versions NRBOAB1 to NRBOAB7; target NRBOAB7, the selected B7 operator | [Summary](0_Hypothesis_Validation/2_TAO/Results/CEC2017_WinTieLoss_Summary.xlsx) / [All dimensions](0_Hypothesis_Validation/2_TAO/Results) |
| `3_delta` | Baseline NRBOAB, earlier decay NRBOABC1 and revised decay NRBOABC2; target NRBOABC2 | [Summary](0_Hypothesis_Validation/3_delta/Results/CEC2017_WinTieLoss_Summary.xlsx) / [All dimensions](0_Hypothesis_Validation/3_delta/Results) |
| `4_DE` | NRBOABC, fixed-control DE version NRBOABCD1 and adaptive DE version NRBOABCD2; target NRBOABCD2 | [Summary](0_Hypothesis_Validation/4_DE/Results/CEC2017_WinTieLoss_Summary.xlsx) / [All dimensions](0_Hypothesis_Validation/4_DE/Results) |
| `5_FINAL` | Revised development version NRBOABCD2 versus the earlier complete ENRBO; target NRBOABCD2 | [Summary](0_Hypothesis_Validation/5_FINAL/Results/CEC2017_WinTieLoss_Summary.xlsx) / [All dimensions](0_Hypothesis_Validation/5_FINAL/Results) |

The initialization A1/A2 names identify initialization alternatives. The same suffixes in the NRSR panel identify search-rule versions. Similarly, `ENRBO` in the `5_FINAL` development panel is the earlier comparator; `ENRBO` in the final comparative and application studies is the final proposed optimizer.

The initialization archive contains workbooks and figures. Its workbooks have two sheets, `Indicators` and `Friedman`, with raw objective statistics and the saved historical run-row ranks. Results are stored directly in the dimension folders. In the original figure names, `收敛图` means convergence plot and `箱线图` means box plot.

## 1 Parameter sensitivity analysis

The [selected sensitivity run](1_Parameter_Sensitivity_Analysis/Results/run_20261028_090507_233) tests nine DF values, 0.1 through 0.9, at dimensions 10, 30, 50 and 100. It uses population 30, iteration-limit input 750 and 30 paired runs. The saved statistical reference is **DF = 0.6**.

| File | What it provides |
|---|---|
| [Summary.xlsx](1_Parameter_Sensitivity_Analysis/Results/run_20261028_090507_233/Summary.xlsx) | Start with `MeanRanks` and `BestObservedDF`; the other sheets are `RankCurvesCI`, `Friedman`, `PairwiseGlobalHolm`, `WinTieLoss` and `Notes` |
| [DF_RankCurve_CI.csv](1_Parameter_Sensitivity_Analysis/Results/run_20261028_090507_233/DF_RankCurve_CI.csv) | Dimension, DF, mean function rank and pointwise 95% bootstrap interval limits |
| [DF_Sensitivity_RankCurves.pdf](1_Parameter_Sensitivity_Analysis/Results/run_20261028_090507_233/DF_Sensitivity_RankCurves.pdf) | Saved four-dimension sensitivity figure |
| `D*/cec2017_Results_D*.xlsx` | Per-function statistics and paired comparisons for one dimension |
| `DF_Sensitivity_Summary.mat` | Binary summary arrays used by the sensitivity analysis |

The DF tests are paired approximate signed-rank tests. The saved Holm adjustment covers all 928 comparisons across the four dimensions. Sheet5 contains paired signed-rank-biserial effects; a positive effect supports the reference DF = 0.6. The plotted confidence intervals are pointwise intervals.

## 2 Comparative experiments

These workbooks compare final ENRBO with NRBO and nine other optimizers. The population-size input is 30, the iteration-limit input is 750, and each algorithm/function combination has 30 runs. The protocol records the algorithm order, numerical metric and stopping settings.

| Suite | Functions | Complete dimension workbooks |
|---|---|---|
| CEC2017 | 29 functions, F1 to F30 with F2 excluded | [10D](2_Comparative_Experiments/CEC2017/Results/D10/cec2017_Results_D10.xlsx) / [30D](2_Comparative_Experiments/CEC2017/Results/D30/cec2017_Results_D30.xlsx) / [50D](2_Comparative_Experiments/CEC2017/Results/D50/cec2017_Results_D50.xlsx) / [100D](2_Comparative_Experiments/CEC2017/Results/D100/cec2017_Results_D100.xlsx) |
| CEC2022 | All 12 functions | [10D](2_Comparative_Experiments/CEC2022/Results/D10/cec2022_Results_D10.xlsx) / [20D](2_Comparative_Experiments/CEC2022/Results/D20/cec2022_Results_D20.xlsx) |

Use Sheet1 for error statistics, Sheet6 for the reported function-block mean ranks, and Sheet4 for Holm-adjusted comparisons. The target in these studies is ENRBO. Each dimension folder also contains function-specific raw records and composite figures.

## 3 Single-strategy contributions

The [single-strategy study](3_Ablation_Study/Results) compares the original NRBO with four independent additions, all at **DF = 0.6**:

| Saved name | Configuration |
|---|---|
| NRBO | Original baseline |
| NRBOA | NRBO with the regression-based NRSR strategy |
| NRBOB | NRBO with the selected TAO strategy |
| NRBOC | NRBO with the feedback decay strategy |
| NRBOD | NRBO with the adaptive DE strategy |

Complete workbooks: [10D](3_Ablation_Study/Results/D10/cec2017_Results_D10.xlsx) / [30D](3_Ablation_Study/Results/D30/cec2017_Results_D30.xlsx) / [50D](3_Ablation_Study/Results/D50/cec2017_Results_D50.xlsx) / [100D](3_Ablation_Study/Results/D100/cec2017_Results_D100.xlsx).

The statistical target here is **NRBO**. Thus, a significant positive target effect supports NRBO; a significant negative effect supports the corresponding added strategy. The protocol and worksheet notes identify the direction used in each display.

## Reading the numerical workbooks

The following conventions apply to the NRSR/TAO/decay/DE development panels, DF study, CEC comparisons and single-strategy additions. Error is `f(x) - f*`, with recorded values below `1e-8` set to zero. Statistics use the 30 saved runs. The earlier initialization workbooks use the raw-objective convention described in Section 0.

| Worksheet | Contents |
|---|---|
| `Sheet1` | Best, worst, mean, median and sample standard deviation of final errors |
| `Sheet2` | Historical mean ranks calculated across run rows, followed by the saved aggregate display |
| `Sheet3` | Unadjusted test p-values and display signs |
| `Sheet4` | Holm-adjusted p-values and corrected comparison decisions |
| `Sheet5` | Effect sizes, with positive values supporting the saved target |
| `Sheet6` | Ranks of the algorithms' mean errors within each function, their dimension-wise averages, and the Friedman test using functions as blocks |

Sheet2 and Sheet6 use different ranking units. For the reported overall numerical comparison, read **Sheet6**. The development, CEC and single-strategy panels use two-sided rank-sum tests, with Holm families covering all functions and opponents within a dimension. Their Sheet3 signs follow mean-error differences and Sheet4 decisions follow adjusted tests and rank effects. In the DF study, both signs use the paired-effect direction. `NS` denotes a non-significant adjusted comparison.

### Shared numerical file dictionary

| Filename or pattern | Contents |
|---|---|
| `CEC2017_Protocol.txt`, `CEC2022_Protocol.txt` | Settings, metric, algorithm order, statistical target and worksheet definitions |
| `CEC*_Experiment_Manifest.mat` | Recorded configuration and implementation/version metadata |
| `cec*_Results_D*.xlsx` | Complete summary and statistical worksheets for one dimension |
| `CEC*_WinTieLoss_Summary.xlsx` | Cross-dimension `Overall`, `ByDimension` and `Notes` sheets |
| `F*_ScoreErrors.csv` | Headerless final-error matrix: rows are run indices; columns follow the saved algorithm order |
| `F*_MeanCurve.csv` | Across-run mean error at the recorded native iteration indices |
| `F*_Raw.mat` | Full stored run values, solutions, convergence arrays, timing, seeds and `algoNames` |
| `Statistics.mat` | Dimension-level descriptive statistics, tests, effects, ranks and Friedman output |
| `CEC*_D*_RadarRanks.csv`, `Radar_AllDimensions.mat` | Rank arrays used for the saved radar plots |
| `CEC*-F*_Combined.*` | Saved function-level composite figures |

For example, [CEC2017 10D F1_Raw.mat](2_Comparative_Experiments/CEC2017/Results/D10/F1_Raw.mat) contains `best_scores` (raw objectives), `scoreErrors`, `best_positions`, `cg_curves`, `curveErrors`, `runSeconds`, `runSeeds` and `algoNames`. Use `algoNames` to identify the algorithm axis: algorithms occupy columns in `scoreErrors` and the third dimension in `best_positions` and `cg_curves`. The original CSV files retain their saved display precision; the MAT arrays preserve the stored double-precision values for tie-sensitive recalculation.

## 4 Qualitative analysis

The manuscript uses [run_20261027_164808_291](4_Qualitative_Analysis/Results/run_20261027_164808_291). It contains 23 classical functions, population 30, 750 iterations and one fixed-seed trajectory per algorithm and function. [Summary.csv](4_Qualitative_Analysis/Results/run_20261027_164808_291/Summary.csv) has 46 rows and identifies the function, dimension, algorithm, seed, final objective, instrumented time and evaluation count.

| File or folder | Contents |
|---|---|
| `Experiment_Manifest.json` / `.mat` | Settings, seed convention, six-output order and source hashes |
| `F*_D*` | One function at its recorded dimension, such as `F1_D30` or `F14_D2` |
| `Raw.mat` | `runs`, `names`, `benchmarkInfo`, `seed` and `settings`; algorithm records contain `bestScore`, `bestPosition`, `curve`, `searchHistory`, `averageFitness` and `firstAgent` |
| `Result_F*.*` | Objective surface, search-history projection, population mean fitness, first-agent coordinate and best-so-far fitness |
| `PopulationDiversity_F*.*` | Saved population-spread curves |
| `ExplorationExploitation_F*.*` | Saved diversity-derived exploration/exploitation indicators |
| `Figure_Captions.txt` | Panel definitions and plotting conventions |
| `NRBO_AlgorithmLog.txt`, `ENRBO_AlgorithmLog.txt` | Saved command-window output |
| `Computed.json`, `Figures_Completed.json`, `Completed.json` | Numerical and figure completion records |

The six algorithm outputs are best score, best position, convergence curve, population history, population-average fitness and first-agent coordinates. Stored population histories contain the resident populations at generation ends. The trajectory display uses the first coordinate of the recorded first agent; the search-history plot projects the population onto two coordinates.

The [other retained qualitative execution](4_Qualitative_Analysis/Results/run_20261027_105706_988) has its own execution records. Both manifests record NRBO DF = 0.6 and ENRBO DF = 0.9. These are descriptive single-run trajectories.

## 5 Application experiments

### Constrained engineering problems

The [final engineering run](5_Application_Experiments/0_2020_RW_Constrained_Optimisation/Results/Run_20261028_073128_834) covers 57 problems and 11 algorithms, with population 40 and 25 trials per problem/algorithm. Per-problem evaluation caps are in [Problems.csv](5_Application_Experiments/0_2020_RW_Constrained_Optimisation/Results/Run_20261028_073128_834/Tables/Problems.csv).

**Start with [Official57_Results.xlsx](5_Application_Experiments/0_2020_RW_Constrained_Optimisation/Results/Run_20261028_073128_834/Official57_Results.xlsx):** read `ReadMe`, `OverallRanks` and `Summary`, then use the other six sheets for detailed records.

| File or directory | Contents |
|---|---|
| [Tables/Summary.csv](5_Application_Experiments/0_2020_RW_Constrained_Optimisation/Results/Run_20261028_073128_834/Tables/Summary.csv) | All 627 problem/algorithm summaries: feasibility, objective/CV statistics, ranks, time and evaluation diagnostics |
| [Tables/OverallRanks.csv](5_Application_Experiments/0_2020_RW_Constrained_Optimisation/Results/Run_20261028_073128_834/Tables/OverallRanks.csv) | Across-problem PM scores, PM positions and descriptive average ranks |
| `Tables/RawRuns.csv` | All 15,675 individual trials, including seeds, retained solutions' objective/CV, feasibility, status, timing and evaluation counts |
| `Tables/BestEncodedVariables.csv` | Coordinates of the selected best trial, identified by `BestTrial`; interpret `EncodedValue` using the official problem encoding |
| `Tables/Constraints.csv` | Constraint residuals and violations for that same selected trial |
| `Tables/Curves.csv` | Evaluation checkpoints with feasible fractions and objective/violation summaries |
| `Tables/PairedSignTests.csv` | Per-problem paired comparisons with ENRBO as target; saved Holm family of 570 tests |
| [Raw records](5_Application_Experiments/0_2020_RW_Constrained_Optimisation/Results/Run_20261028_073128_834/Raw) | Individual files named `RCxx_ALGORITHM_nn.mat`, with trial indices 01 to 25 |
| `Results.mat` | Aggregate binary results, tracked with Git LFS |
| `ScoreInputs.mat` | Saved arrays and outputs of the PM scoring calculation |
| [Protocol.txt](5_Application_Experiments/0_2020_RW_Constrained_Optimisation/Results/Run_20261028_073128_834/Protocol.txt), `Protocol.mat` | Actual settings, constraint handling, retention rules and seed records |
| `Official_Submission` | Objective and violation matrices in `_F.txt` and `_CV.txt` files: ten evaluation-checkpoint rows and 25 trial columns |
| `SourceHashes.csv`, `SourceSnapshot/Official` | Source provenance and retained official problem materials |
| `Reports`, completion records | Saved analysis and execution status |

`FR` is the feasible fraction over all 25 trials. `CV` is the mean of the retained violation vector, including zero entries; `CV = 0` identifies a feasible point under the recorded rules. Feasibility-first ordering places feasible trials by objective, followed by infeasible trials by violation. The best/median/worst F and CV columns are paired values from that ordering; mean and SD summarize all retained trials.

`OfficialPM` is the inherited column name for the study's generalization of the released scoring procedure to these 11 algorithms. Lower PM is better. The `Raw` files preserve each trial's retained point, constraints and recorded traces. Use `BestTrial` in the variables/constraints tables to locate the selected trial's raw file. As a single-trial example, [RC03_ENRBO_01.mat](5_Application_Experiments/0_2020_RW_Constrained_Optimisation/Results/Run_20261028_073128_834/Raw/RC03_ENRBO_01.mat) contains the `record` struct, including `best.f`, `best.cv`, `best.z`, `best.g`, `best.h`, timing and evaluation counts. The engineering `Figures` directory is retained as an empty directory.

### Grid-map path planning

Use [Validation50_Uniform_20261030_205554_362](5_Application_Experiments/1_Path_Planning/Results/Validation50_Uniform_20261030_205554_362) for the final 50-map results. The five families are WAREHOUSE, PARKING, ROOMS, GATE and CITY, with ten layouts each and square grids of 40, 60, 80 or 100 cells. The eleven stochastic algorithms use population 50, 30 paired runs per map and 50,050 counted objective evaluations per run.

**Start with [Results.xlsx](5_Application_Experiments/1_Path_Planning/Results/Validation50_Uniform_20261030_205554_362/Results.xlsx), [Algorithm_Overall.csv](5_Application_Experiments/1_Path_Planning/Results/Validation50_Uniform_20261030_205554_362/Analysis/Algorithm_Overall.csv) and the [raw-result overview image](5_Application_Experiments/1_Path_Planning/Results/Validation50_Uniform_20261030_205554_362/Overview/Raw_Primary_Overview.png).**

| File or directory | Contents |
|---|---|
| [Tables/Scenarios.csv](5_Application_Experiments/1_Path_Planning/Results/Validation50_Uniform_20261030_205554_362/Tables/Scenarios.csv) | Map IDs, sizes, obstacle counts, optimization dimension, budgets and provenance |
| [Protocol.mat](5_Application_Experiments/1_Path_Planning/Results/Validation50_Uniform_20261030_205554_362/Protocol.mat) | Frozen occupancy grids, endpoints, configuration and hashes |
| `Tables/Protocol.csv` | Human-readable settings |
| `Tables/Summary.csv` | Per-map/per-algorithm results for all three postprocessing states |
| `Tables/RawRuns.csv` | 49,500 state records from 16,500 stochastic runs, including failures, status and diagnostic fields |
| `Tables/SmoothingPairs.csv` | One paired before/after record for each stochastic run |
| `Tables/RawAverageRanks.csv` | Per-map raw feasibility-first descriptive ranks |
| `Tables/AverageRanks.csv` | Per-map ranks after two shortcut passes |
| [Analysis](5_Application_Experiments/1_Path_Planning/Results/Validation50_Uniform_20261030_205554_362/Analysis) | Primary raw-outcome summaries and statistical comparisons |
| `Analysis/Feasibility_McNemar_Holm500.csv` | All 500 exact paired raw-success comparisons |
| `Analysis/Raw_Quality_Sign_Holm500.csv` | All 500 exact paired raw-quality comparisons, with its own Holm family |
| `Analysis/Per_Map_Success_Counts.csv` | All algorithms' success counts on each map |
| `Analysis/Algorithm_By_Family.csv`, `Success_By_Grid_Size.csv` | Success summaries by map family and grid size |
| `Analysis/Raw_Primary_Ranks_FullPrecision.csv` | Raw ranks recomputed from full-precision records |
| `Analysis/Paired_MapBootstrap_Conditional_10000.csv` | Saved paired-map bootstrap comparisons |
| `Analysis/Smoothing_Before_After_Preferences.csv` | Changes in paired preferences after smoothing |
| `Analysis/Runtime_Diagnostics.csv`, `Nonempty_Warnings.csv` | Run status, invalid calls and diagnostics; the warnings table retains nonempty warning rows |
| `Tables/PairedTests.csv` | Saved quality tests for the two-pass state, identified by `PostPasses = 2` |
| `Tables/AStar.csv` | Separate deterministic A* reference results |
| [Figures](5_Application_Experiments/1_Path_Planning/Results/Validation50_Uniform_20261030_205554_362/Figures) | One folder per map, with representative paths, smoothing pairs and performance figures |
| [Raw](5_Application_Experiments/1_Path_Planning/Results/Validation50_Uniform_20261030_205554_362/Raw) | Individual stochastic and A* records |
| `AllResults.mat` | Complete final aggregate, tracked with Git LFS |
| `Audit`, `SourceHashes.csv`, `Tables/Files.csv` | Saved layout, source-fidelity and validation records |

All stochastic searches use `SearchPasses = 0`. `PostPasses = 0, 1, 2` denote the raw route and one or two shortcut passes applied to the same candidate. Success requires a completed, nonempty endpoint-to-endpoint path with no colliding segment. Success fractions include all 30 runs; length and geometry summaries use feasible routes. A fraction of `0.90`, for example, means 90% success. Undefined feasible-route summaries are saved as `NaN`.

Raw and two-pass ranks describe different states; lower ranks are better. Feasible routes rank by length ahead of failures, with failures tied last. Use the files under `Analysis` for the primary raw-success and raw-quality comparisons. The workbook's `PairedTests` sheet identifies its two-pass endpoint explicitly. A* is a separate reference outside the eleven-optimizer ranking, with its own graph-expansion and time records. Application times are elapsed measurements from concurrent-worker runs.

To inspect one run, use its map ID, algorithm and trial index to locate `Raw/<Map>_<Algorithm>_S0_<nn>.mat`. Its `record` contains the seed, `bestX`, three `paths` and three `metrics` entries. `bestX` holds ten row/column waypoint pairs; each saved route includes start and goal. The small `Protocol.mat` and a single raw record are sufficient for checking one map/run.

The [earlier path-planning run](5_Application_Experiments/1_Path_Planning/Results/Run_20261030_153005_472) retains development layouts. Some map IDs are reused across runs with different geometry, so keep the run-folder ID with the map ID. [Export_Check](5_Application_Experiments/1_Path_Planning/Results/Export_Check) contains figure/spreadsheet export checks.

## File formats

| Extension | How to read it |
|---|---|
| `.xlsx` | Download and open in Excel or a compatible spreadsheet viewer; the named sheets organize the study results |
| `.csv` | View or download the table; use UTF-8 when importing filenames containing Chinese characters |
| `.pdf`, `.png` | Saved figures for viewing; the available formats follow each original experiment |
| `.fig` | MATLAB-editable figure |
| `.mat` | Binary arrays, structures and histories; MATLAB reads the saved formats, including v7.3 summaries |
| `.json`, `.txt`, `.md` | Settings, captions, execution records, analyses and explanatory documents |
| `.docx` | The official benchmark revision log retained in the engineering snapshot |
| `.gitkeep` | Empty-directory marker |

The two zero-byte `RUNNING.lock` files are archived status markers. Completion files and run protocols document the saved executions. Source-hash tables can name `.m` files from the evaluated projects; the optimizer source files themselves are excluded from this results repository.

## Downloading the results

For individual checks, use the workbook, CSV, figure and raw-record links above. Three aggregate MAT files use Git Large File Storage (Git LFS): the engineering `Results.mat` and the two path runs' `AllResults.mat`. Each is available through its GitHub download button.

To obtain the complete archive with the original large binary files:

```bash
git lfs install
git clone -c core.longpaths=true https://github.com/Albert1-29/ENRBO-for-Complex-Engineering-Optimization-Using-Dzhanibekov-Inspired-Trap-Avoidance.git ENRBO-results
cd ENRBO-results
git lfs pull
```

A Git LFS pointer is a short text record containing `version`, `oid` and `size`. If a downloaded aggregate MAT contains that text, retrieve its binary content with Git LFS or the file's download button. After downloading the binaries, compare file sizes and SHA-256 values against [RESULTS_MANIFEST.csv](RESULTS_MANIFEST.csv).

The [original result manifest](RESULTS_MANIFEST.csv) covers all 57,352 source result files. The [verified upload snapshot](https://github.com/Albert1-29/ENRBO-for-Complex-Engineering-Optimization-Using-Dzhanibekov-Inspired-Trap-Avoidance/tree/ea6fc29ca04d44bc65415d1eb0a1c29b6d7386e4) fixes that result set. The original experiment projects and saved data were preserved during publication. Retained benchmark materials carry their original notices.
