## **1\. Cell types identified at different stages of infection**

Using neighbourhood clustering and marker-based annotation of the scRNA-seq data, multiple epithelial and immune cell populations were identified across the course of SARS-CoV-2 infection:

* Mock (uninfected control):

   The epithelial landscape is dominated by well-defined ciliated cells, goblet cells, club (Clara) cells, basal cells, and a small population of ionocytes. These clusters exhibit stable transcriptional identities, reflecting a homeostatic bronchial epithelium with minimal immune cell presence.

* 1 dpi (early infection):

   Core epithelial populations (ciliated, goblet, club, and basal cells) remain present, but early transcriptional perturbations emerge. Ionocytes and secretory cells show increased relevance due to their association with ACE2 expression. Early recruitment of myofibroblasts and low numbers of macrophages are detectable, reflecting initial host responses to viral entry.

* 2 dpi (peak infection):

   This stage shows extensive cellular diversification and disruption. Alongside epithelial populations, there is a notable expansion of macrophages and other immune-associated clusters. Ciliated and goblet cells are heavily represented, consistent with their vulnerability to infection and involvement in viral replication. Metabolically active epithelial subsets become more prominent.

* 3 dpi (late infection / recovery phase):

   Immune populations, particularly macrophages, are expanded, indicating inflammatory dominance. Goblet cells remain abundant, consistent with mucus hypersecretion. Importantly, club cells and basal cells become more prominent, reflecting epithelial regeneration and repair. Overall cluster separation partially re-emerges, suggesting recovery from acute transcriptional stress.

---

## **2\. Why these cell types correlate with COVID-19 infection**

The identified cell types correlate strongly with COVID-19 infection due to their biological roles and receptor expression profiles:

* Ciliated and goblet cells form the primary barrier of the airway epithelium and are directly exposed to inhaled pathogens, making them key targets for SARS-CoV-2.

* Ionocytes and secretory cells express ACE2 and TMPRSS2 at higher levels, facilitating viral entry.

* Macrophages expand as part of the innate immune response, contributing to inflammation, cytokine signalling, and viral clearance.

* Club and basal cells act as progenitor populations and become more prominent during recovery, supporting epithelial regeneration after viral injury.

Thus, the temporal changes in these populations reflect the progression from viral entry, through peak infection and inflammation, to tissue repair.

---

## **3\. Is ACE2 a good marker for tracking COVID-19 infection rate in this dataset?**

Based on this dataset, ACE2 is not a reliable marker for tracking infection rate over time.

Although ACE2 is essential for viral entry, its expression is:

* Low and restricted to specific epithelial subsets at baseline,

* Transiently detectable early in infection,

* Downregulated following viral entry due to receptor internalisation, epithelial damage, or cell death.

As a result, ACE2 expression does not scale proportionally with viral burden or disease progression, particularly at later time points. Therefore, ACE2 is better interpreted as a susceptibility or entry marker, rather than a dynamic indicator of infection severity.

---

## **4\. Difference between ENO2 and ACE2 as biomarkers in the two studies**

ACE2 and ENO2 represent fundamentally different biological processes:

* ACE2 is a viral entry receptor, whose expression reflects cellular susceptibility to SARS-CoV-2 infection. Its levels are tightly regulated and often decrease after infection, limiting its utility as a longitudinal marker.

* ENO2 (enolase 2\) is a metabolic enzyme associated with glycolysis and cellular stress. Its upregulation reflects metabolic reprogramming, inflammation, and increased energetic demand during infection.

In contrast to ACE2, ENO2 shows broader and more sustained expression changes, making it a more informative marker of cellular state, metabolic stress, and disease progression, rather than viral entry alone.

---

## **5\. Cell cluster with the highest ACE2 abundance after 3 dpi and biological interpretation**

At 3 dpi, ACE2 expression is overall low but remains most detectable within residual secretory/club cell associated clusters rather than heavily infected ciliated populations.

Visual interpretation:

* On the UMAP, ACE2 signal appears sparse and localised, rather than widespread.

* High-ACE2 clusters do not overlap with strongly inflammatory or macrophage-dominated regions.

Biological interpretation:

* Cells with high ACE2 at 3 dpi likely represent less-infected or regenerating epithelial cells, rather than actively infected ones.

* This suggests that cells expressing ACE2 earlier in infection may have been depleted through apoptosis or immune clearance.

* The persistence of ACE2 in club or secretory cells may reflect epithelial renewal and restoration of normal airway function.

