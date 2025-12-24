# Multi-Modal Trajectory Analysis of SARS-CoV-2 Infection in Human Airway Epithelium
**HackBio Internship | Stage Three: Advanced scRNA-seq Analysis**
## Overview

This repository presents a computational re-analysis and reconstruction of the single-cell transcriptional landscape of SARS-CoV-2 infection. Utilizing 10X Genomics scRNA-seq data, this study models the dynamic transition of bronchial epithelial cells from a homeostatic state to peak viral response.

Key Focus: Beyond cluster identification, this analysis investigates the immunometabolic shift occurring during infection, specifically characterizing the correlation between viral entry susceptibility **(ACE2)** and glycolytic activation **(ENO2)**.

---

## Objectives

***Decipher Cellular Heterogeneity:** Identify and annotate major bronchial epithelial and recruited immune cell populations across the longitudinal infection course using Leiden clustering and marker-based validation.

***Map Infection Kinetics:** Characterize the global transcriptional remodeling occurring from early viral entry (1 dpi) to peak inflammatory response (3 dpi).

***Reconstruct Cellular State Transitions:** Utilize **Diffusion Pseudotime (DPT)** to infer high-resolution trajectories, modeling the continuous path from homeostatic epithelium to infected states.

***Profile the Immunometabolic Axis:** Evaluate the expression dynamics of **ACE2** (viral susceptibility) and **ENO2** (glycolytic activation) to identify metabolic signatures of cellular stress and viral hijacking.

***Optimize Large-Scale scRNA-seq Workflows:** Implement a modular computational pipeline to manage high-dimensional data (~77,000 cells) within resource-constrained cloud environments.

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

The workflow was implemented using **Scanpy** and optimized for high-dimensional data management in cloud environments.

**1. Computational Optimization:** Due to the high memory footprint of the integrated 10X Genomics dataset (~77,000 cells), the pipeline was executed via a **modular, time-point-specific approach**. This ensured high-fidelity preprocessing and normalization of individual conditions (Mock through 3 dpi) prior to trajectory reconstruction.

**2. Data Integrity and QC** * 
**Resolution of Sample Mislabeling:** Identified and corrected metadata discrepancies in the source dataset through iterative marker-based annotation.

**Stringent Filtering:** Removed doublets using **Scrublet** and excluded cells with >10% mitochondrial content to ensure biological signal outweighed technical noise.

**3. Advanced Trajectory Analysis**
**State Transitions:** Utilized **Diffusion Pseudotime (DPT)** to model the continuous transcriptional path from epithelial homeostasis to peak viral response.

**4. Immunometabolic Profiling**

**Glycolytic Shift:** Evaluated the expression dynamics of ACE2 and ENO2 to correlate viral entry susceptibility with infection-induced metabolic reprogramming.





---

## Key Biological Findings

***Non-Linear Correlation of Viral Entry:** ACE2 expression defines initial cellular susceptibility but does not strictly predict late-stage viral burden. This suggests that post-entry intracellular factors, rather than just receptor density, dictate the peak of infection.

***Infection-Induced Glycolytic Switch:** Identified a significant and progressive upregulation of **ENO2 (Enolase 2)** along the pseudotime trajectory. This transcriptional signature indicates a **metabolic reprogramming towards glycolysis**, likely to meet the biosynthetic and energetic demands of rapid viral replication and inflammatory signaling.

***Temporal Resolution of Lung Remodeling:** Pseudotime analysis successfully resolved the transition from epithelial homeostasis (Mock) to a peak inflammatory state (3 dpi), characterized by the emergence of **pro-inflammatory macrophage populations** and goblet cell hyperplasia.

---

## Key Visual Outputs

**Figure 1: Spatiotemporal Mapping of Infection Progress and Metabolic Reprogramming**
<img width="1446" height="369" alt="image" src="https://github.com/user-attachments/assets/4be4bcf7-adba-45d0-95f8-a5c4f3383cde" />

<img width="1446" height="369" alt="image" src="https://github.com/user-attachments/assets/afa3a3ec-caa3-45b6-9357-aeb1316e6a3e" />

<img width="1446" height="369" alt="image" src="https://github.com/user-attachments/assets/75afbeb3-6f1f-4d15-a45b-2617a3e81fd9" />

<img width="1446" height="369" alt="image" src="https://github.com/user-attachments/assets/bf8b7889-7b0c-4995-9d4b-2e4f6c7091d4" />

**Description:**

**Condition (Left):** Global UMAP embedding showing the transition of cells across the four longitudinal stages: Mock, 1dpi, 2dpi, and 3dpi.

**ACE2 (Center):** Expression density of the SARS-CoV-2 entry receptor, identifying susceptible cell populations.

**ENO2 (Right):** Expression of Enolase 2, acting as a transcriptional proxy for the glycolytic shift and metabolic reprogramming observed during peak infection.

**Figure 2: Pseudotemporal Reconstruction of Cellular State Transitions**
<img width="959" height="369" alt="image" src="https://github.com/user-attachments/assets/2ba43df3-f5cb-4ec9-85b2-88df4658066e" />
<img width="931" height="369" alt="image" src="https://github.com/user-attachments/assets/543a6adc-79a4-4343-8b9e-93309160080d" />
<img width="997" height="369" alt="image" src="https://github.com/user-attachments/assets/5d6fa9ef-af66-4fe0-bbcc-0559d421c0b9" />


**Description:**

**Sequential Infection Kinetics:** This panel series demonstrates the Diffusion Pseudotime (DPT) progression across the first 48 hours of infection. By ordering cells from Mock through 2 dpi, we can visualize the initial departure from homeostasis.

**Trajectory Initialization:** The transition from purple (low pseudotime) to green (increasing pseudotime) identifies the early "tipping point" where epithelial cells begin transcriptional remodeling in response to viral entry.

**Lineage-Specific Dynamics:** The inclusion of structural **Myofibroblasts** and **Alveolar Type II cells** across these timepoints establishes the foundational path of the infection. This early-phase modeling captures the critical window where metabolic shifts begin to accelerate.

**Progression toward Peak Infection:** This 0–48 hour trajectory serves as the baseline for the experiment, mapping the continuous cellular states that ultimately culminate in the peak inflammatory response observed at the 3 dpi terminal state.


**Figure 3: Transcriptional Drivers of the Metabolic and Inflammatory Shift**
<img width="2850" height="369" alt="image" src="https://github.com/user-attachments/assets/285c10dd-6c2d-4ab9-87b0-20b14edea051" />
<img width="2837" height="369" alt="image" src="https://github.com/user-attachments/assets/74fae2a3-3876-4ea1-b5f6-708cfc252ea7" />



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

