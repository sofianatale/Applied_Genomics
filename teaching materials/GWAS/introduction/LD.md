# Structure of Common Genetic Variation: Linkage Disequilibrium (LD)

## Introduction
In **Genome-Wide Association Studies (GWAS)**, the structure of genetic variation in the population under investigation is a key element.  
Not all variants are inherited independently: some are transmitted together across generations.  
This non-random association of alleles is known as **Linkage Disequilibrium (LD)**.  

Understanding LD is critical because:
- It allows us to reduce the number of genotyped markers by focusing on representative **tag SNPs**.  
- It explains why GWAS signals typically appear as **clusters of associated SNPs**, rather than single isolated variants.  
- It helps distinguish between **causal variants** and **proxy variants** that are correlated due to LD.

## Basic Concepts

### Allele and Haplotype Frequencies
- Consider **two SNPs**, each with two alleles:
  - SNP1: M1 / m1
  - SNP2: M2 / m2
- Allele frequencies:  
  - $q_1$ = frequency of allele M1  
  - $q_2$ = frequency of allele M2  
- Haplotype frequency:  
  - $q_{12}$ = frequency of haplotype M1M2  

### Linkage Equilibrium
- If SNP1 and SNP2 are independent:  
  $q_{12} = q_1 \cdot q_2$  
- In this case, the alleles assort randomly, and $D = 0$.

### Linkage Disequilibrium
- **Deviation from independence** is measured by statistic $D$:  
  $D = q_{12} - q_1 q_2$  
- If $D \neq 0$, the SNPs are correlated.

## Standardized LD Measures

Since $D$ depends on allele frequencies, standardized measures are used:

- **D′ (D prime)**  
  - Scales $D$ between 0 and 1.  
  - $D′ = 1$ → perfect linkage (no recombination between the alleles).  
  - $D′ = 0$ → alleles are independent.  

- **$r^2$ (squared correlation coefficient)**  
  - Expresses how much the variation at one SNP predicts the variation at the other.  
  - $r^2 = 1$ → SNPs provide identical information.  
  - $r^2 = 0$ → SNPs are completely unlinked.  
  - In practice, GWAS often consider SNPs with $r^2 > 0.8$ as strongly correlated.  

## Example of LD Calculation

Imagine we genotype **10 individuals** for two SNPs, A and B:

| Sample | SNP_A | SNP_B | Haplotype |
|--------|-------|-------|-----------|
| 1      | TT    | GG    | TG        |
| 2      | TG    | GA    | TA        |
| 3      | TG    | GG    | TG        |
| ...    | ...   | ...   | ...       |
| 10     | GG    | AA    | GA        |

- Allele frequencies:  
  - $p_A(T) = 0.8$, $p_A(G) = 0.2$  
  - $p_B(G) = 0.7$, $p_B(A) = 0.3$

- Expected haplotype frequency under equilibrium:  
  $$
  p_{TG} = p_A(T) \cdot p_B(G) = 0.8 \cdot 0.7 = 0.56
  $$

- Observed haplotype frequency: $0.70$  

- Difference:  
  $$
  D = 0.70 - 0.56 = 0.14
  $$  

This positive $D$ indicates that SNP_A and SNP_B are in **linkage disequilibrium**.

## Visual Representation of LD

1. **LD Heatmaps**  
   - Pairwise LD between SNPs is computed across a genomic region.  
   - Results are displayed in a triangular **heatmap**:
     - Dark red = strong LD (high correlation).  
     - White/light colors = weak LD (low correlation).  
   - **Blocks of LD** can be identified, corresponding to genomic segments inherited together.

2. **Indirect Association**  
   - Often the SNP genotyped in a GWAS is **not the causal SNP**.  
   - Instead, it lies in **high LD** with the true disease-causing variant.  
   - The genotyped SNP acts as a **proxy marker** for the causal one.

   Example:  
   - **Genotyped SNP** → included in the SNP panel.  
   - **Causal SNP** → not directly genotyped, but in high LD.  
   - The genotyped SNP shows statistical association because it tracks the causal allele.

## Role of LD in GWAS

1. **Efficient Genotyping**
   - By identifying **tag SNPs** (representative SNPs in LD blocks), GWAS can capture most of the variation without genotyping every SNP.
   - This reduces cost and effort while preserving information.

2. **Interpretation of Results**
   - Significant SNPs in a GWAS peak often represent **indirect associations**.  
   - The true causal variant may not be genotyped, but lies within the same LD block.  
   - Peaks in **Manhattan plots** are usually composed of multiple SNPs in strong LD.

3. **Filtering Redundancy**
   - If multiple SNPs are perfectly correlated ($r^2 \approx 1$), only one needs to be tested.  
   - This avoids redundant data and reduces the multiple testing burden.

## Summary

- **LD** is the non-random association of alleles at different loci.  
- It is measured by **$D$, $D′$, and $r^2$**.  
- **High LD** means variants are correlated and transmitted together.  
- In GWAS:
  - LD allows efficient genotyping with **tag SNPs**.  
  - Significant associations may reflect **indirect effects** through LD.  
  - Peaks of association in Manhattan plots arise because several SNPs in a block are linked.  
- Understanding LD is essential to move from **associated SNPs** to identifying the **true causative variants and genes**.
