# A small GWAS on 1000 Genomes, with a South Asian focus

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Gsb057/gwas-1000g-south-asia/blob/main/gwas_1000g_south_asia.ipynb)

An end-to-end genome-wide association study (GWAS) in one Python notebook, using **PLINK 2**
on public **1000 Genomes Phase 3** data (2,504 people, 26 populations). The data includes
five South Asian groups: Gujarati, Punjabi, Bengali, Sri Lankan Tamil and Telugu.

**Steps:** quality control (missing data, MAF, Hardy-Weinberg) → PCA of ancestry →
association test, with and without ancestry correction → Manhattan and QQ plots.

**Run it:** click *Open in Colab*, then `Runtime → Run all` (about 10-15 min, nothing to install).

## Results

On 1000 Genomes chromosome 22 (2,504 people), quality control kept 170,052 of 1,055,454 SNPs.
PCA separated the continents, and South Asians fell between Europeans and East Asians.
With a simulated trait containing 10 true SNPs plus an ancestry effect:
  - without ancestry correction: lambda = 44.5, 63484 SNPs below 5e-8
  - with 10 PCs as covariates:   lambda = 1.11, 367 SNPs below 5e-8, true SNPs found: 6/10

All plots are in the notebook.

## Key design choices
* **Simulated trait.** 1000 Genomes records no traits, so the notebook builds one from
  10 known SNPs plus an ancestry-linked shift. Knowing the truth lets us check the GWAS,
  and the ancestry shift shows why PCs are needed (population stratification).
* **Chromosome 22 only**, to keep the run short. Change `CHROM` in the first cell for another chromosome.
* **Reproducible:** pinned PLINK version (2.00a5.12), fixed random seed, all settings in one
  cell, data downloaded straight from the official 1000 Genomes server.

## Limitations
Simulated trait, one chromosome, about 2,500 people, and a linear model with PCs rather than a mixed model.

## Data and tools
1000 Genomes Project Consortium (2015), *Nature* 526:68-74 · Chang et al. (2015), Second-generation PLINK, *GigaScience* 4:7
