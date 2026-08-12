# sc-RNAseq-Scanpy-analysis

**Single-Cell RNA-Seq Analysis with ScanPy**

A hands-on practice notebook for processing and analyzing **single-cell RNA-sequencing (scRNA-seq)** data using the [ScanPy](https://scanpy.readthedocs.io/) framework — a standard toolset for single-cell genomics.

## 📦 Contents

| File | Description |
|------|-------------|
| `sc-sequence.ipynb` | End-to-end scRNA-seq analysis workflow |

## 🧬 Analysis Workflow

The notebook walks through the standard scRNA-seq analysis pipeline:

1. **Data loading** — loads publicly available 10x Genomics scRNA-seq samples via `pooch` (from a Figshare repository);
2. **QC metric calculation** — computes mitochondrial, ribosomal, and hemoglobin gene percentages for quality assessment;
3. **Quality visualization** — violin plots and scatter plots of QC metrics (genes per cell, total counts, mitochondrial %);
4. **Cell & gene filtering** — removes low-quality cells and rarely expressed genes;
5. **Doublet detection** — uses **Scrublet** to identify and remove doublets;
6. **Normalization** — library-size normalization (`normalize_total`) followed by log transformation, with raw counts preserved in a separate layer for downstream use.

## 🛠 Requirements

- Python 3.8+
- [scanpy](https://scanpy.readthedocs.io/)
- [anndata](https://anndata.readthedocs.io/)
- [pooch](https://www.fatiando.org/pooch/)
- [numpy](https://numpy.org/)

Install with:

```bash
pip install scanpy anndata pooch numpy
```

## 🚀 Quick Start

```python
import scanpy as sc
import pooch

# Load example data
adata = ...   # see notebook for data loading
# QC
sc.pp.calculate_qc_metrics(adata, qc_vars=["mt", "ribo", "hb"], log1p=True)
# Filter
sc.pp.filter_cells(adata, min_genes=100)
# Normalize
sc.pp.normalize_total(adata)
sc.pp.log1p(adata)
```

## 📄 License

For educational and research purposes.
