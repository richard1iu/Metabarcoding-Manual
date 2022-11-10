# Microbiome Analysis Method

## 1.Co-occurrence Network Analysis

### 1) spearman/pearson correlation
R package: {base}/{WGCNA}  
`{WGCNA}` is much more rapid than R `{base}` package

### 2) SparCC (Sparse Correlations for Compositional data)
R package: [{SpiecEasi}](https://github.com/zdk123/SpiecEasi)  

Pearson correlation of the **compositional data based on relative fractions of genes** can produce unreliable results  

SparCC estimate correlations from **compositional data** based on 
1. the log-ratio transformation
2. iterating to find the strongest correlated OTU pair

### 3) SPIEC-EASI (SParse InversE Covariance Estimation for Ecological Association Inference)
R package: [{SpiecEasi}](https://github.com/zdk123/SpiecEasi)  

**Very slow** for SpiecEasi_method = ‘glasso’ for a large number of taxa.  

It **infer** an underlying graphical model using **conditional independence**   

Two network construction approaches based on **graph model**：
1. neighborhood selection
2. sparse inverse covariance selection.  

### 4) MENA (Molecular ecological network analyses)
A [online pipeline](http://ieg4.rccc.ou.edu/mena/)  

It construct network through **Random Matrix Theory (RMT)-based methods**.  

This approach automatically defined **correlation threshold** between paired taxa and is robust to noise

### 5) FlashWeave
R package: [{FlashWeave}](https://github.com/meringlab/FlashWeave.jl)  

a **julia** package. (relative diffcult to install)  

It is a **probabilistic graph-based method** to obtain the conditional independence.  

It **predicts** direct relationships among taxa based on compositional abundance data (OTU table).  

**prerequisite:**
1. install julia language in your computer and add the julia in the computer path
2. install {FlashWeave} R package.

### 6) beemStatic
R package: [{beemStatic}](https://github.com/CSB5/BEEM-static)  

It infer interaction network of **cross-sectional** datasets based on the **generalized Lotka-Volterra model**   

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
