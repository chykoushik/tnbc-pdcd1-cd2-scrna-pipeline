# TNBC PDCD1/CD2 scRNA-seq Pipeline

Computational pipeline for the paper:

> **Computational Stratification and Engineering Translation of the
> PDCD1/CD2 Immune Axis in Triple-Negative Breast Cancer**
> Koushik Chowdhury, M.Sc. — Universität des Saarlandes



---
## Interactive Dashboard

**Live:** [https://chykoushik.github.io/tnbc-pdcd1-cd2-scrna-pipeline/tnbc_dashboard.html](https://chykoushik.github.io/tnbc-pdcd1-cd2-scrna-pipeline/tnbc_dashboard.html)

Open in any browser for a full visual summary of all results including
patient stratification, ARI/NMI validation, survival curves, LR proxy
screen, DesignPriorityScore rankings, and bootstrap stability.

## Overview

End-to-end single-cell RNA-seq analysis pipeline applied to the
GSE176078 TNBC atlas (100,064 cells, 26 patients) that translates
single-cell immune phenotypes into per-patient synthetic immune-cell
engineering recommendations via the PDCD1/CD2 axis.

**Pipeline stages:**
1. QC filtering and atlas construction
2. Leiden clustering and annotation validation (ARI/NMI)
3. T cell extraction and re-embedding
4. Exhaustion and cytotoxicity module scoring
5. CD8 state stratification (quantile-based, q=0.75)
6. Patient-level feature aggregation
7. TCGA-BRCA cross-modal survival validation (Cox/KM)
8. Targeted ligand-receptor proxy screen
9. DesignPriorityScore and bootstrap stability analysis (n=200)

---

## Repository Structure

```
tnbc-pdcd1-cd2-scrna-pipeline/
│
├── GSE176078.zip            # Full analysis notebook with all outputs
│                            # and figures (extract to get GSE176078.ipynb)
├── tnbc_dashboard.html      # Interactive results dashboard
├── README.md
├── LICENSE                  # MIT
│
└── outputs/                 # Tabular results (also on Harvard Dataverse)
    ├── patient_strata_tcell_cd8_exhaustion.csv
    ├── patient_strata_design_targets_rulebased.csv
    ├── patient_design_priority_scores.csv
    ├── patient_tcell_features.csv
    ├── cluster_label_agreement_ARI_NMI.csv
    ├── exhaustion_threshold_stability.csv
    ├── bootstrap_top3_stability.csv
    ├── axis_vs_exhaustion_spearman.csv
    ├── LR_targeted_strengths_all_groups.csv
    ├── LR_targeted_ranked_top200.csv
    ├── LR_targeted_ligand_sources_top5.csv
    └── cluster_markers_top20.csv
```

> **Note:** The notebook is provided as `GSE176078.zip` (includes all
> cell outputs and figures). Download and unzip to open in Google Colab
> or Jupyter. Tabular outputs are also deposited at Harvard Dataverse.

---

## Interactive Dashboard

Open `tnbc_dashboard.html` in any browser for a full visual summary
of all results including patient stratification, ARI/NMI validation,
survival curves, LR proxy screen, DesignPriorityScore rankings, and
bootstrap stability.

---

## Data

| Source | Access |
|--------|--------|
| GSE176078 (scRNA-seq) | [NCBI GEO](https://ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE176078) |
| TCGA-BRCA (bulk RNA-seq) | [UCSC Xena](https://xena.ucsc.edu/) |
| Output CSVs | [Harvard Dataverse](https://doi.org/10.7910/DVN/XXXXXXX) |

Primary data are not included in this repository.
Download GSE176078 files from NCBI GEO into your Google Drive
before running the notebook:

```
MyDrive/GSE176078/
├── count_matrix_sparse.mtx
├── count_matrix_genes.tsv
├── count_matrix_barcodes.tsv
└── metadata.csv
```

TCGA-BRCA expression and survival data are downloaded automatically
inside the notebook via `wget` from UCSC Xena.

---

## Requirements

Python 3.10 · Google Colab (GPU runtime recommended)

The first cell of the notebook installs all dependencies and mounts
Google Drive automatically:

```bash
pip install scanpy==1.9.8 anndata==0.9.2 leidenalg igraph \
    umap-learn scipy pandas numpy matplotlib seaborn \
    lifelines statsmodels scikit-learn
```

| Package | Version |
|---------|---------|
| Scanpy | 1.9.8 |
| AnnData | 0.9.2 |
| NumPy | 1.24.4 |
| Pandas | 1.5.3 |
| SciPy | 1.10.1 |
| scikit-learn | 1.2.2 |
| Matplotlib | 3.7.2 |
| Seaborn | 0.12.2 |
| Lifelines | 0.27.8 |
| statsmodels | 0.13.5 |

---

## Usage

1. Clone this repository or download `GSE176078.zip` directly

```bash
git clone https://github.com/chykoushik/tnbc-pdcd1-cd2-scrna-pipeline.git
```

2. Unzip the notebook

```bash
unzip GSE176078.zip
```

3. Download GSE176078 files from NCBI GEO into
`MyDrive/GSE176078/` on your Google Drive

4. Open `GSE176078.ipynb` in Google Colab

5. Run cells top to bottom — Drive mounts and paths are
set automatically in the first cell

---

## Key Outputs

| File | Description |
|------|-------------|
| `patient_design_priority_scores.csv` | DesignPriorityScore ranking for all 26 patients |
| `patient_strata_design_targets_rulebased.csv` | Per-patient engineering recommendations |
| `cluster_label_agreement_ARI_NMI.csv` | ARI/NMI annotation validation |
| `bootstrap_top3_stability.csv` | Bootstrap ranking stability (n=200) |
| `LR_targeted_ranked_top200.csv` | Ligand-receptor proxy screen results |

---

## Citation

If you use this code or outputs, please cite:

```bibtex
@article{chowdhury2025tnbc,
  author  = {Chowdhury, Koushik},
  title   = {Computational Stratification and Engineering Translation
             of the PDCD1/CD2 Immune Axis in Triple-Negative Breast Cancer},
  journal = {[]},
  year    = {2026},
  doi     = {[]}
}
```

---

## License

MIT License — see `LICENSE` for details.

---

## Contact

Koushik Chowdhury · Universität des Saarlandes
ORCID: [0009-0007-6319-3769](https://orcid.org/0009-0007-6319-3769)
