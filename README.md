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

## Pipeline

```
Data → EDA
```

---

## Setup

```bash
uv run jupyter notebook elliptic_fraud_detection.ipynb
```
