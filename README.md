# Supplementary Material: A Hybrid Multiscale Framework for Cancer Progression: Coupling Boolean Networks with Cellular Potts Models

This repository contains the source code, simulation configuration files, and analytical pipelines used in the study:

**A Hybrid Multiscale Framework for Cancer Progression: Coupling Boolean Networks with Cellular Potts Models"**

![GitHub Logo](https://github.com/yourusername/multiscale-cell-cycle/blob/main/Cover_figure.png)


## Overview

The scripts and configuration files provided here allow for the reproduction of all simulations and analyses presented in the study. The simulation couples a Boolean stochastic regulatory network (MaBoSS) with a spatial agent-based cell simulation (CompuCell3D) to model epithelial growth, contact inhibition via the Hippo-YAP pathway, and the transition from normal to cancerous phenotypes.

## Abstract

In this study a multiscale framework, coupling a Cellular Potts Model with Boolean regulatory networks was developed, to simulate cell cycle signaling across seven modeled progressive mutational stages of carcinogenesis. By simulating cell cycle progression under varying boolean networks topology, it has shown that pre-malignant networks exhibit remarkable dynamic plasticity, activating compensatory molecular feedback loops to maintain phenotypic control.Conversely, the transition to advanced cancer completely shuts down the cell's internal brakes, causing the tumor to grow uncontrollably regardless of high cell density.At the tissue scale, these molecular shifts alter cell cycle subpopulations, changing a quiescent monolayer into actively dividing cells in a stage-dependent manner. This confirms that early mutations cause a compensated hyperproliferative state. Furthermore, the sharp increase in the Proliferation Index and the distorted $G1/S$ ratio support the hypothesis that malignant transformation requires crossing a threshold toward full autonomy, insulating cells from microenvironmental constraints.
## Contents

- `/Notebook/`: Base simulation data analysis project directory.
- `/Data/`: Simulation data for modeled different cancer progression stages
  - `Data_cell_layer/`: Directory with time series of cell cycle phases for normal cells.
  - `Data_molecular_layer/`: Directory with time series of changes in probability of activation for all nodes of boolean network.
- `/results/`: Outputs of simulation analysis results

## Model Components

### Boolean Network Nodes

| Node | Function |
|------|----------|
| Cyclin D (CycD) | Sensor of growth factors; promotes G1/S transition |
| Cyclin E (CycE) | G1/S progression |
| Cyclin A (CycA) | S phase and G2/M progression |
| Cyclin B (CycB) | G2/M transition |
| Rb | Tumor suppressor; binds and inhibits E2F |
| E2F | Transcription factor activating S-phase genes |
| p27 | CDK inhibitor; blocks G1/S |
| Cdc20, Cdh1, UbcH10 | APC/C regulators controlling cyclin degradation |
| NF2, LATS, YAP | Hippo pathway mediating contact inhibition |

### Order Parameters

| Parameter | Description |
|-----------|-------------|
| AUC (Area Under Curve) cell layer | Total biomass produced over simulation time |
| W_AUC | Integrative fitness = AUC_cancer / AUC_normal |
| Proliferation Index (PI) | Fraction of cells in S+G2+M phases |
| Quiescence Index (QI) | Fraction of cells in G0 phase |
| Mitotic Index (IM) | Fraction of cells in M phase |
| G1/S Ratio | Ratio of cells in G1 to S phase |
| G2/M Ratio | Ratio of cells in G2 to M phase |

## Requirements

The simulations and analyses were performed using:

- **CompuCell3D version 4.2.4 or higher** (for spatial simulations)
- **MaBoSS** (integrated with CompuCell3D for Boolean stochastic simulations)
- **Python 3.x** with the following libraries:
  - `pandas` (Data processing)
  - `numpy` (Numerical computations)
  - `scipy` (Integration, curve fitting, optimization)
  - `matplotlib` / `seaborn` (Visualization)
  - `networkx` (network working)
  - `os` / `sys` (manipulating files)

## Usage

```bash
git clone https://github.com/ChristianQF/multiscale-cell-cycle.git
cd multiscale-cell-cycle
```

### Output Data Format

`celltype_distribution-01.csv` and `celltype_distribution-02.csv` contain:

| Column | Description |
|--------|-------------|
| MCS | Monte Carlo Step (simulation time) |
| TotalCells | Total number of living cells |
| NonCycling | Cells in G0 phase (quiescent) |
| CycleG1 | Cells in G1 phase (growth) |
| CycleS | Cells in S phase (DNA synthesis) |
| CycleG2 | Cells in G2 phase (preparation for mitosis) |
| CycleM | Cells in M phase (mitosis) |


## Citation

If you use this code or the generated datasets in your research, please cite:

> Solis-Calero, Christian (2026). Multiscale Modeling of Cell Cycle and Cell Growing Dynamics in Carcinogenesis: Integrating Boolean Stochastic Networks with Agent-Based Cell Simulation. [Institution Name].

---
**Contact:** [csolisc@unmsm.edu.pe] for any inquiries regarding the implementation or data.
