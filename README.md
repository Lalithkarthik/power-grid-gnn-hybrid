# Hybrid GNN–Solver Framework for Power Grid Optimization

A modular, scalable framework that integrates Graph Neural Networks (GNNs) with classical Optimal Power Flow (OPF) solvers to enable fast, physics-aware, constraint-compliant power grid optimization.  
This repository also includes an optional PPO-based reinforcement learning module for dynamic grid control.

---

## Key Features

- **Graph-Based Power Grid Modeling**
  - Bus and line feature extraction
  - Graph construction utilities

- **Multiple GNN Architectures**
  - GCN  
  - GraphSAGE  
  - GAT  

- **Hybrid OPF Optimization**
  - GNN produces a warm-start for the solver
  - Classical AC-OPF solver guarantees feasibility

- **Reinforcement Learning (Optional)**
  - PPO agent for adaptive, dynamic control
  - Grid2Op-based simulation environment

- **Scalable & Modular**
  - Works on IEEE 14/30/57/118/300-bus systems
  - Clean module separation for research and extension

---

##  Project Structure

project/
│
├── src/
│ ├── data/
│ │ ├── dataset_loader.py # Load OPF datasets, Grid2Op data
│ │ ├── preprocess.py # Cleaning, normalization
│ │ └── graph_builder.py # Build graph: nodes, edges, features
│ │
│ ├── models/
│ │ ├── gcn.py # Graph Convolutional Network
│ │ ├── graphsage.py # GraphSAGE (inductive)
│ │ ├── gat.py # Graph Attention Network
│ │ └── hybrid_solver.py # GNN→OPF integration logic
│ │
│ ├── rl/
│ │ ├── ppo_agent.py # PPO implementation
│ │ └── environment.py # Grid2Op environment wrapper
│ │
│ ├── solvers/
│ │ ├── opf_solver.py # AC-OPF solver (PYPOWER)
│ │ └── warmstart.py # GNN → solver warm-start utilities
│ │
│ ├── utils/
│ │ ├── metrics.py # MAE, MAPE, runtime metrics
│ │ ├── visualization.py # Plots and analysis
│ │ ├── config.py # Centralized hyperparameters
│ │ └── logger.py # Logging and experiment tracking
│ │
│ └── main.py # Entrypoint for training & evaluation
│
├── notebooks/
│ └── power_grid_v7.ipynb # Original exploratory notebook
│
├── experiments/
│ ├── logs/ # Training & solver logs
│ ├── results/ # Plots, tables, evaluation data
│ └── checkpoints/ # Saved GNN/RL model weights
│
├── data/
│ ├── raw/ # PGLib, Grid2Op raw data
│ ├── processed/ # Saved processed tensors
│ └── synthetic/ # Optional synthetic networks
│
├── tests/
│ ├── test_gnn.py
│ ├── test_opf.py
│ ├── test_rl.py
│ └── test_utils.py
│
├── requirements.txt
├── README.md
└── LICENSE


---

## ⚙️ Installation

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```

### 1. Install dependencies
```bash
pip install -r requirements.txt
```




