# Microbiome Analysis Method

## 1.Co-occurrence Network Analysis

### 1) spearman/pearson correlation
R package: {base}/{WGCNA}  
`{WGCNA}` is much more rapid than R `{base}` package

### 2) SparCC (Sparse Correlations for Compositional data)
R package: [{SpiecEasi}](https://github.com/zdk123/SpiecEasi)  

Pearson correlation of the **compositional data** can produce unreliable results since the observed data take the form of **relative fractions** of genes or species, rather than their absolute abundances.

SparCC is design for estimating correlations from **compositional data** based on 
1. the log-ratio transformation
2. iterating to find the strongest correlated OTU pair

### 3) SPIEC-EASI (SParse InversE Covariance Estimation for Ecological Association Inference)
R package: [{SpiecEasi}](https://github.com/zdk123/SpiecEasi)  

**Very slow** for SpiecEasi_method = ‘glasso’ for a large number of taxa.  

It **infer** an underlying graphical model using the concept of **conditional independence** instead of correlation between taxa.  

This package has two network construction approaches based on **graph model**：
1. neighborhood selection
2. sparse inverse covariance selection.  

### 4) MENA (Molecular ecological network analyses)
a online platformhttp://ieg4.rccc.ou.edu/mena/  

It construct network through **Random Matrix Theory (RMT)-based methods**.  

This approach is remarkable in that the **correlation threshold** between paired taxa is automatically defined and robust to noise

### 5) FlashWeave
R package: [{FlashWeave}](https://github.com/meringlab/FlashWeave.jl)  

a **julia** package. (relative diffcult to install)  

It is a **probabilistic graph-based method** to obtain the conditional independence.  

It **predicts** direct relationships among taxa based on compositional abundance data (OTU table) through statistical co-occurrence.  

**prerequisite:**
1. install julia language in your computer and add the julia in the computer path
2. install {FlashWeave} R package.

### 6) beemStatic
R package: [{beemStatic}](https://github.com/CSB5/BEEM-static)  

It can be applied to **cross-sectional** datasets to infer interaction network based on the generalized **Lotka-Volterra model**   

It is typically used in the microbial **time-series** data and thus the network is **directed**.  

## Diff ASV
- LEfSe
- Stamp
- edgeR
- machine learning


## Similarity of group
- ANOSIM
- PERMANOVA
- Amova
- MRPP

## Significant factors
- envfit {vegan}
- bioenv {vegan}
- machine learning
- regression model
