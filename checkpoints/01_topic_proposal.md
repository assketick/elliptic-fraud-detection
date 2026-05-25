# Checkpoint 1 — Topic Proposal
**Course:** Social Network Analysis, HSE  
**Student:** Nikita Tukhlin

---

## Topic

**Elliptic Bitcoin Fraud Detection**  
Detecting fraudulent transactions in the Bitcoin network using graph analysis methods and GNNs.

---

## Research Question

> Can the graph structure of Bitcoin transactions improve fraud detection compared to standard ML trained only on node features?

---

## Dataset

**Elliptic Bitcoin Dataset** (Weber et al., 2019)  
[https://www.kaggle.com/datasets/ellipticco/elliptic-data-set](https://www.kaggle.com/datasets/ellipticco/elliptic-data-set)

- 203 769 transaction nodes, 234 355 edges
- 49 timesteps (temporal graph)
- 165 features per node (72 of which are pre-aggregated neighbour features)
- Labels: illicit (4 545, ~10%), licit (42 019, ~90%), unknown (157 205)

The dataset is suitable for the task because:
- It contains a real network structure (Bitcoin transactions)
- It has binary labels (fraud / not fraud)
- It is large enough for GNNs yet can be processed on CPU/MPS

---

## Methods (plan)

| Step | Method |
|---|---|
| EDA | Degree distribution (log-log), centrality, k-core, Louvain, temporal |
| Baseline | Logistic Regression, CatBoost on node features |
| H2 | CatBoost + topological features (PageRank, degree, community, k-core) |
| H3 | GraphSAGE (2-layer, mean aggregation) |

**Metric:** F1-score for the `illicit` class — the dataset is imbalanced (~10% fraud).

---

## Hypotheses

- **H1:** Fraud nodes have statistically significantly different degree/betweenness from licit nodes (Mann-Whitney U)
- **H2:** Adding topological features improves the classifier's F1-illicit
- **H3:** GraphSAGE outperforms the baseline on F1-illicit
