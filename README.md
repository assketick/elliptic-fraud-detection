# Elliptic Bitcoin Fraud Detection
### Social Network Analysis — Course Project, HSE 2026

**Research question:** Can the graph structure of Bitcoin transactions improve fraud detection compared to standard ML trained only on node features?

---

## Dataset

[Elliptic Bitcoin Dataset](https://www.kaggle.com/datasets/ellipticco/elliptic-data-set) — a graph of real Bitcoin transactions labelled as fraud / licit.

| | |
|---|---|
| Nodes (transactions) | 203 769 |
| Edges | 234 355 |
| Timesteps | 49 |
| Features per node | 165 |
| illicit (fraud) | 4 545 (9.8%) |
| licit | 42 019 (90.2%) |
| unknown | 157 205 |

> Data not included in the repository due to size (658 MB).  
> Download instructions: [`data/README.md`](data/README.md)

---

## Structure

```
├── elliptic_fraud_detection.ipynb   # Main notebook (EDA → models → results)
├── data/
│   └── README.md                   # How to download data
├── checkpoints/
│   ├── 01_topic_proposal.md        # Checkpoint 1 — topic (May 6)
│   └── 02_eda_summary.md           # Checkpoint 2 — EDA (May 20)
└── requirements.txt
```

---

## Pipeline

```
Data → EDA → Hypotheses → Baseline → Graph Features → GNN (GraphSAGE, GAT) → Ablation → Conclusions
```

## Results

| Model | F1-illicit |
|---|---|
| CatBoost (node features) | **0.785** |
| CatBoost + graph features | 0.778 |
| GraphSAGE 2-layer (PyTorch) | 0.709 |
| GAT 2-layer (PyTorch) | 0.551 |
| Logistic Regression + graph features | 0.344 |
| Logistic Regression (baseline) | 0.333 |

**Key finding (ablation):** removing the 72 pre-aggregated neighbour features hurts the
GNNs more than CatBoost (GraphSAGE −0.153, GAT −0.263 vs CatBoost −0.085). The graph
methods leaned on the pre-baked aggregates, and the raw graph (avg degree 2.3, very
sparse) is too thin for message passing to beat gradient boosting.

---

## Setup

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook elliptic_fraud_detection.ipynb
```
