# Microbiome Advanced Analysis Methods

## 1.Co-occurrence Network Analysis

### 1) Spearman/pearson correlation
R package: `{base}` | `{WGCNA}`  
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

### 7) LSA (local similarity analysis)

Python script: [ELSA](https://bitbucket.org/charade/elsa/src/master/)

The analysis is only carried out for the time gradient samples such as growth, season, and treatment cycle.

1. Based on the absolute abundance table of species, F-function transformation is carried out first to distinguish the data characteristics of biological duplication and time gradient. 
2. Then calculate the LSA score between species in combination with time gradient and Pearson correlation, and take the value [- 1,1]. 
3. Then conduct the replacement test to calculate the P value, and finally output the significantly correlated data used to draw the network diagram.

## 2. Microbial community assembly methods

### 1) Null model
R package: [{microeco}](https://chiliubio.github.io/microeco/)  

Infer the strength of **five ecological process** dominating the community assembly under the specific hypothesis (Stegen et al. 2013).

based on **βNTI**(beta nearest taxon index) and **RCbray**(Bray-Curtis-based Raup-Crick).

The approach for phylogenetic signal analysis is based on the mantel correlogram (Liu et al. 2017)

### 2) binning
R package: [{iCAMP}](https://github.com/DaliangNing/iCAMP1)  

Infer community assembly mechanisms using phylogenetic **bin-based** null model analysis

### 3) NST (normalized stochasticity ratio)
R package: [{NST}](https://cran.r-project.org/web/packages/NST/index.html)  

taxonomic and phylogenetic normalized stochasticity ratio

### 4) NCM (neutral community model)


### 5) SIMPER/Per-SIMPER
R package: [{DNCImper}](https://github.com/Corentin-Gibert-Paleontology/DNCImper)  

Based on similarity index, SIMPER estimate the contributions of taxa to the overall dissimilarity between groups of assemblages.  

Per-SIMPER compare **empirical SIMPER plot** with **randomized plots** computed by matrix permutation of the empirical matrix.  

The closer the random profile to the empirical one, the more niche and/or dispersal processes played a role in the assemblage construction.

### 6) DNCI (Dispersal Niche Continuum Index)
R package: [{DNCImper}](https://github.com/Corentin-Gibert-Paleontology/DNCImper)  

DNCI transform the **qualitative results** into a **quantitative index** based on PerSIMPER function. 

## 3.Diff ASV
>A [paper](https://www.nature.com/articles/s41467-022-28034-z) published in nature communitication compared the performance of 14 different differential abundance testing method on 38 16S rRNA gene datasets. They found `ALDEx2` and `ANCOM-II` produce the most consistent results across studies and agree best with the intersect of results from different approaches. 
It is necessary to adopt a consensus preprocess approach to help ensure robust biological interpretations.

### Normalization
- TMM: The weighted Trimmed Mean of M-values
- RLE: Relative Log Expression; R package `{DESeq}` or `{edgeR}`
- UQ: Upper-Quartile; R package `{DESeq}` or `{edgeR}`
- TSS: Total Sum Normalization; R package `{hilldiv}`
- CSS: Cumulative Sum Scaling; R package `{metagenomeSeq}`
- VST: Variance Stabilizing Transformation; R package `{DESeq}`
- CLR: Centered Log-Ratio; R package `{ALDEx2}`
### Differential abundance test
- LEfSe
- Stamp
- edgeR
- DESeq2
- limma voom 
- ALDEx2
- ANCOM-II
- metagenomeSeq
- Machine learning


## 4.Similarity of group
- ANOSIM
- PERMANOVA
- Amova
- MRPP

## 5.Significant factors
- envfit; R package `{vegan}`
- bioenv; R package `{vegan}`
- machine learning
- regression model

## 6.Niche width
- Levins’ and Shannon-Wiener niche breadth index; R package `{spaa}`
- distinguish generalist和specialist; R package `{EcolUtils}`

## 7.indicator taxa
- Threshold Indicator Taxa ANalysisl; R package `{TITAN2}`
- ;R package  {indicspecies}
