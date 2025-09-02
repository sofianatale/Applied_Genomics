# Genome-Wide Association Studies (GWAS)

## Introduction
The goal of genetics is to identify **genetic risk factors** for both:
- **Common, complex diseases**
- **Rare Mendelian disorders**

To achieve this, different **study designs, technologies, and analytical tools** can be used.  
One of the most powerful approaches is the **Genome-Wide Association Study (GWAS)**, which analyzes **DNA sequence variation across the genome** in order to identify risk factors for diseases that are **common in the population**.

GWAS integrates:
- **Genotypic data** (genetic information of individuals)
- **Phenotypic data** (observable traits such as disease status, height, weight, etc.)

## The Common Disease / Common Variant (CD/CV) Hypothesis

The **CD/CV hypothesis** states that **common disorders are likely influenced by genetic variation that is also common in the population**.

### Key points
1. If **common genetic variants influence disease**, the **effect size** (or penetrance) of any one variant must be **small** compared to rare disorders.
2. If **common alleles have small genetic effects (low penetrance)**, but disorders still show **heritability**, then **multiple variants must contribute**.  
   - Each SNP contributes a small proportion of risk.  
   - The overall **heritability** comes from the combined, **polygenic effect** of many variants.

### Conceptual Spectrum
- **Rare variants**: often have **large effects** (e.g., Mendelian mutations).  
- **Common variants**: usually have **small effects**, but act together to shape risk.  
Relationship between allele frequency and effect size: most GWAS hits are **common variants with small effects**.*

## Requirements for GWAS

To test the **CD/CV hypothesis**, GWAS requires a **systematic approach**:

1. **Location and density of SNPs**  
   Identify commonly occurring SNPs to be examined by genetic studies.

2. **Population-specific differences**  
   Catalog genetic variation across populations, since allele frequencies differ by ancestry.

3. **Correlations among genetic variants**  
   Determine correlations to avoid collecting **redundant information**.

4. **Reference datasets**  
   Projects such as the **International HapMap Project** were designed to map common variation and **characterize correlations among variants**.

## Linkage Disequilibrium (LD)

GWAS relies heavily on the concept of **Linkage Disequilibrium (LD)**.

- **Definition**: LD is the **non-random association of alleles at different loci**.  
- If two variants are inherited together more often than expected by chance, they are said to be **in LD**.

### How it works
- During **recombination**, alleles are reshuffled.  
- Over generations, recombination breaks down associations.  
- However, some SNPs remain **correlated** due to physical proximity or low recombination rates.

### LD in Families vs Populations
- **Within a family**: linkage means markers stay together through inheritance.  
- **Within a population**: LD decays over generations, as recombination events reduce correlation.

## Summary

- **GWAS** enables the discovery of variants associated with common phenotypes.  
- The **CD/CV hypothesis** explains why most GWAS hits are common variants with small effects.  
- **Population differences** and **LD patterns** must be considered in study design.  
- The combined contribution of many common alleles explains the **polygenic architecture** of most complex diseases.
