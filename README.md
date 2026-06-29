# Unsupervised Learning: Clustering and Dimensionality Reduction

## Overview
This project explores unsupervised machine learning across three datasets of increasing complexity. Three clustering algorithms (K-Means, DBSCAN, Hierarchical) and three dimensionality reduction techniques (PCA, t-SNE, UMAP) are applied and compared, with a focus on when to use each method and how to interpret the results.

## Datasets
| Dataset | Description | Source |
|---|---|---|
| Mall Customers | Demographic and spending data for 200 customers | Kaggle |
| Spotify Tracks | Nine audio features per track (danceability, energy, tempo, etc.) | Spotify Web API |
| 3D Mammoth | ~10,000-point 3D point cloud for dimensionality reduction benchmarking | MNoichl / GitHub |

Data files are not included in this repository. All datasets download automatically via `gdown` or `wget` when running the notebook.

## Methods

**Clustering:**
- **K-Means** — partition-based; uses the elbow method to identify optimal K
- **DBSCAN** — density-based; identifies clusters of arbitrary shape and flags outliers
- **Hierarchical (Agglomerative)** — builds a nested cluster tree using Ward linkage; compared against K-Means via Adjusted Rand Index

**Dimensionality Reduction:**
- **PCA** — linear projection; loadings interpreted to identify which features drive each principal component
- **t-SNE** — non-linear; emphasizes local neighborhood structure
- **UMAP** — non-linear; balances local and global structure preservation

## Key Findings
- K-Means on the mall dataset identifies five distinct customer archetypes (e.g., high income/high spending, low income/high spending) consistent across runs
- DBSCAN successfully identifies the same natural groupings while labeling boundary points as noise — without requiring K to be specified upfront
- Hierarchical and K-Means cluster assignments show high agreement (Adjusted Rand Index reported in notebook)
- For the Spotify dataset, clusters correspond to interpretable audio profiles (e.g., high danceability/low acousticness vs. high instrumentalness/low speechiness)
- On the 3D mammoth benchmark, t-SNE best separates anatomical structures; UMAP preserves global shape better; PCA collapses the non-linear manifold

## How to Run

**Option 1 — Google Colab (recommended)**
1. Upload `Clustering_and_Dimensionality_Reduction.ipynb` to Google Colab
2. Run all cells top to bottom — all datasets download automatically

**Option 2 — Local environment**
```bash
git clone https://github.com/yourusername/clustering-dimensionality-reduction
cd clustering-dimensionality-reduction
pip install -r requirements.txt
jupyter notebook Clustering_and_Dimensionality_Reduction.ipynb
```

## Tools & Libraries
| Library | Purpose |
|---|---|
| `pandas` / `numpy` | Data manipulation |
| `matplotlib` / `seaborn` | Visualization |
| `scikit-learn` | K-Means, DBSCAN, Hierarchical, PCA, t-SNE, preprocessing |
| `umap-learn` | UMAP dimensionality reduction |

## Project Structure
```
clustering-dimensionality-reduction/
├── README.md
├── Clustering_and_Dimensionality_Reduction.ipynb
├── requirements.txt
├── data/       # Not tracked — datasets download automatically
└── figures/    # Output plots (optional)
```
