# Data

Dataset: **Elliptic Bitcoin Dataset**  
Source: [Kaggle](https://www.kaggle.com/datasets/ellipticco/elliptic-data-set)

## Download

```bash
# Via Kaggle CLI (requires API key at ~/.kaggle/kaggle.json)
kaggle datasets download ellipticco/elliptic-data-set
unzip elliptic-data-set.zip -d elliptic_bitcoin_dataset/
```

Or manually via browser from the same Kaggle page.

## Files

After extracting, place in `data/raw/`:

| File | Size | Description |
|---|---|---|
| `elliptic_txs_features.csv` | 658 MB | 203 769 transactions × 167 columns (txId, timestep, f1–f165) |
| `elliptic_txs_edgelist.csv` | 4.3 MB | 234 355 edges (source, target) |
| `elliptic_txs_classes.csv` | 3.2 MB | Node labels (1=illicit, 2=licit, unknown) |

> `elliptic_txs_features.csv` is excluded from git (658 MB exceeds GitHub's limit).  
> The other two files are committed to the repository.
