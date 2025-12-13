
# Stage Three HackBio: SARS-CoV-2 Single-Cell Trajectory Analysis

## Overview

This repository contains a reproducible single-cell RNA-sequencing (scRNA-seq) analysis of SARS-CoV-2 infection dynamics in human bronchial epithelial cells. The study reproduces and extends the trajectory-based framework described by **Ravindra et al. (2021)**, leveraging longitudinal scRNA-seq data collected at multiple infection time points.

Cells were profiled under four conditions: mock (uninfected), 1 day post-infection (1 dpi), 2 days post-infection (2 dpi), and 3 days post-infection (3 dpi). The analysis reconstructs infection-driven transcriptional trajectories, identifies major airway and immune cell populations, and characterises key molecular markers associated with viral entry and metabolic reprogramming.

---

## Objectives

* Identify major epithelial and immune cell types in the human airway.
* Characterise transcriptional changes across progressive stages of SARS-CoV-2 infection.
* Infer pseudotemporal trajectories reflecting infection-induced cellular state transitions.
* Compare **ACE2** (viral entry susceptibility) and **ENO2** (metabolic activation) expression dynamics.
* Visualise infection-associated transcriptional remodelling using UMAP and pseudotime analyses.

---

## Dataset

**Source:** NCBI GEO — GSE166766
**Technology:** 10X Genomics scRNA-seq

| Sample     | Condition | Approx. Cells |
| ---------- | --------- | ------------- |
| GSM5082289 | Mock      | ~17,000       |
| GSM5082290 | 1 dpi     | ~18,000       |
| GSM5082291 | 2 dpi     | ~20,000       |
| GSM5082292 | 3 dpi     | ~22,000       |

Raw count matrices were provided in `.mtx` and `.tsv` formats.


## Analysis Pipeline

The workflow was implemented using **Scanpy** and optimised for execution on **Google Colab (TPU-compatible)**.

1. **Environment Setup**
   Installation of Scanpy, Scrublet, Decoupler, and supporting libraries.

2. **Data Loading**
   Independent ingestion of raw count matrices for each infection condition.

3. **Quality Control**
   Removal of cells with fewer than 200 detected genes or >10% mitochondrial content.

4. **Normalisation & Feature Selection**
   Library-size normalisation, log transformation, and selection of the top 2,000 highly variable genes.

5. **Dimensionality Reduction**
   PCA, nearest-neighbour graph construction, and UMAP embedding.

6. **Clustering**
   Leiden clustering to identify transcriptionally distinct populations.

7. **Cell Type Annotation**
   Reference-based annotation using PanglaoDB and CellMarker databases.

8. **Trajectory Inference**
   Diffusion pseudotime (DPT) analysis to reconstruct infection-driven trajectories.

9. **Differential Expression Analysis**
   Identification of genes associated with progression from mock to 3 dpi.

10. **Dropout Bias Assessment**
    Evaluation of zero-inflation effects in ACE2 and ENO2 expression.

11. **Visualisation**
    Generation of UMAPs, pseudotime gradients, violin plots, and expression trendlines.

---

## Key Biological Findings

* **ACE2** expression marks cellular susceptibility to SARS-CoV-2 entry but does not directly reflect infection burden due to dropout effects and post-entry regulation.
* **ENO2** expression increases progressively along pseudotime, peaking at late infection stages, consistent with infection-induced metabolic reprogramming.
* Pseudotime trajectories capture a transition from epithelial homeostasis (mock) to viral replication (2 dpi) and immune-dominated inflammation with early repair signatures (3 dpi).
* Goblet and ciliated epithelial cells emerge as key targets during late infection, while macrophages dominate inflammatory states.

---

## Key Visual Outputs

* **UMAP embeddings** showing clustering by infection stage and cell type.
* **Pseudotime gradients** illustrating infection progression from mock to 3 dpi.
* **ACE2 and ENO2 expression trends** plotted along pseudotime.
* **Dropout histograms** assessing sparsity in lowly expressed genes.

---

## Reproducibility

Install dependencies using:

```bash
pip install -r requirements.txt
```

Session information is logged via:

```python
import session_info
session_info.show()
```

### Recommended Environment

* Python ≥ 3.9
* Scanpy ≥ 1.9.3
* Decoupler ≥ 1.6.0
* Matplotlib ≥ 3.8.0
* Seaborn ≥ 0.13.0

---

## Reference

Ravindra, N. G. et al. (2021). *Single-cell longitudinal analysis of SARS-CoV-2 infection in human bronchial epithelial cells*. **PLOS Biology**.


## Credits

* **Dataset:** Ravindra et al., PLOS Biology (2021)
* **Analysis Framework:** HackBio Stage Three
* **Tools:** Scanpy, Decoupler, Matplotlib, Seaborn

