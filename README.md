# Hybrid GNN–Solver Framework for Power Grid Optimization

A modular, scalable framework that integrates Graph Neural Networks (GNNs) with classical Optimal Power Flow (OPF) solvers to enable fast, physics-aware, constraint-compliant power grid optimization.  
This repository also includes an optional PPO-based reinforcement learning module for dynamic grid control.


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

## Installation

### 1. Clone the repository
```bash
git clone https://github.com/Lalithkarthik/power-grid-gnn-hybrid.git
cd power-grid-gnn-hybrid
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Train GNN Models
Train a specific GNN:
```bash
python src/main.py --train-gnn --model gcn
python src/main.py --train-gnn --model graphsage
python src/main.py --train-gnn --model gat
```
Training outputs include:
1. Loss curves
2. MAE & MAPE metrics
Saved weights in experiments/checkpoints/

### 4. Run the hybrid GNN-OPF solvers
```bash
python src/main.py --run-hybrid --model gat
```
This will:
1. Load the trained GNN
2. Predict near-optimal OPF variables
3. Warm-start the AC-OPF solver
4. Output feasibility metrics and runtime
5. Save results to experiments/results/

### 5. Train the PPO RL Agent
```bash
python src/main.py --train-rl
```
This launches:
1. Grid2Op simulation
2. PPO training loop
3. Epioodic reward tracking
4. Model checkpoints

### 6. Dataset Setup
Place all raw datasets (PGLib OPF, Grid2Op, etc.) inside:
```bash
data/raw/
```
After running preprocessing:
```bash
data/processed/
```
will contain graph tensors, feature matrices, and normalized values.

### 7. Evaluation
Evaluation includes:
1. Prediction Accuracy
- MAE, MAPE for voltages & dispatch
2. Hybrid Solver Metrics
- Runtime
- Solver iteration count
- Constraint violations
3. Scaling Tests
- Runtime vs bus count
- GNN generalization

### 8. Testing
Run all unit tests:
```bash
python tests/
```

### 9. Configuration
All hyperparameters are stored inside:
```bash
src/utils/config.py
```
This includes:
1. Learning rates
2. Hidden dimensions
3. Number of GNN layers
4. PPO settings
5. File paths






