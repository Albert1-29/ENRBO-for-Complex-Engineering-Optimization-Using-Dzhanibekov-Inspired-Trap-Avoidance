# CEC2020-RW 官方57题工程实验

在MATLAB打开根目录 **main.m**，点击Run。已有未完成实验会自动续跑，完成的独立运行不重复计算。

```text
5_Application_Experiments/
├─ main.m        唯一完整运行入口
├─ README.md
├─ Algorithms/   最终ENRBO及10个对照算法，搜索源码保持原样
├─ Official/     官方57题评价器、数据、指南和排名源码
├─ Scripts/      执行、记录、表格、绘图和进度查询
├─ Docs/         协议说明与源码差异记录
└─ Results/      按时间戳保存每轮完整结果
```

## 实验设置

- 问题：RC01—RC57，全部来自官方Cal_par.m和cec20_func.m。
- 每算法每问题25次独立运行。
- 最大评价次数：D≤10为100000；10<D≤30为200000；30<D≤50为400000；50<D≤150为800000；D>150为1000000。初始化和重复点计入；不再统一为1000代。
- 种群40。官方允许自行选择种群，并未规定40。
- 沿用11个算法：ENRBO、AROA、BKA、CFO、DOA、IVYA、NRBO、PSA、TOC、WaOA、WO。ENRBO的DF=0.9，原NRBO为0.6。
- 所有算法使用相同标量搜索包装：f+100000×Σv²。罚系数是本研究沿用设置，不是官方规定。报告将目标值与违反量分开。
- 初次启动用时间产生根种子，保存全部配对随机种子；续跑保持原种子。
- 最多24个并行工作进程；无并行工具箱时串行运行。AROA需要Statistics and Machine Learning Toolbox。

全部57题、11算法、25次，共15675次独立运行、5417500000次候选评价。完整实验可能持续较长时间，运行中可打开Scripts/check_status.m查询进度。中断后重新点main.m续跑。

## 输出

每轮Results/Run_时间戳包含：

- Raw：每次独立运行的原始MAT记录，完成后立即落盘。
- Tables：汇总、逐次结果、约束、编码变量、收敛曲线及统计检验CSV。
- Official57_Results.xlsx：统一Excel结果。
- Official_Submission：每算法每题F和CV文件，按官方要求为10×25矩阵，对应0.1—1.0倍评价预算。
- Figures：可选绘图目录；运行Scripts/redraw_figures.m后保存FIG、矢量PDF、300dpi PNG。
- Reports/Detailed_Results_Analysis.md：完成全部数值运行后自动生成总体及逐题分析。
- Protocol.mat/txt、SourceHashes.csv、SourceSnapshot：完整参数、种子和源码快照。
- Progress.json：当前进度。NUMERICS_COMPLETED.txt表示数值及表格完成；COMPLETED.txt表示所有输出完成。

图片导出：完成数值实验后，在MATLAB图形界面打开Scripts/redraw_figures.m运行，无需重跑算法。FIG按可见状态保存。默认完整计算先输出官方数值文件和分析，不依赖后台图形服务。

## 官方版本

官方仓库：https://github.com/P-N-Suganthan/2020-RW-Constrained-Optimisation

固定提交：a148874a233f9fb8fa82fdae3b5739d1bba7020d。

官方评价文件不作数学修正。RC12的22次方、RC22有符号误差、RC44约束数量差异均按原源码保留，详见Docs/Protocol_and_Source_Notes.md。因此新结果不能与上一轮修正模型结果混比。

旧项目（包括全部旧Results）已完整备份到D:\Codex\Backups\Engineering_Before_Official57_20261027_204020\Project。
