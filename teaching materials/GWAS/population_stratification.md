# Population Stratification in GWAS

## Introduction
**Population stratification** occurs when a study population contains **multiple subgroups** (e.g., individuals of different ethnic or genetic background).  

- If allele frequencies differ between subpopulations, this can create **spurious associations** (false positives) or mask true associations.  
- Ensuring that all individuals come from a **consistent genetic background** is essential for reliable GWAS results.  

> Example: in a case–control GWAS, if more cases are sampled from one subpopulation and controls from another, allele frequency differences may reflect ancestry rather than the trait under study.  

## Why It Matters
- Genetic structure can **inflate false positive rates** if not corrected.  
- Population stratification is an **essential QC step** in any GWAS.  
- If ignored, you may incorrectly conclude that many SNPs are associated with a phenotype, when in reality the effect is due to population differences.  

## Detecting Population Stratification

### Multidimensional Scaling (MDS) Approach
- MDS calculates the **genome-wide average proportion of alleles shared** between pairs of individuals.  
- Produces **quantitative indices** (components) summarizing genetic variation.  
- These components can be plotted to visualize clusters of individuals who are genetically more similar to each other than expected.  

#### How it works
1. Start with a matrix of individuals × SNPs.  
2. Reduce matrix dimensionality (dimensional reduction).  
3. Plot individuals in 2D or 3D → clusters indicate population substructure.  

Example: with 150,000 SNPs, you can summarize genetic similarity in just two dimensions.  

## Real Example (Mouse GWAS)
A GWAS was carried out to study body weight in different mouse strains:  
- Almost all SNPs appeared associated with body weight.  
- This suspicious result was due to **population structure**: different strains had different genetic backgrounds **and** body weight distributions.  

Visualization showed:  
- **Two major clusters** (subpopulations).  
- Within each cluster, individuals were genetically similar and had similar body weights.  
- Across clusters, differences in genetics and phenotype overlapped → leading to spurious associations.  

**Takeaway**: If population structure is not corrected, GWAS results may reflect **ancestry differences** instead of true genotype–phenotype associations.  


## Statistical Correction Methods

### Genomic Control (Inflation Factor λGC)
- Compares the median of observed test statistics to that expected under the null hypothesis.  
- If $\lambda_{GC} > 1$: indicates inflation due to stratification or unmeasured confounding.  
- If $\lambda_{GC} < 1$: suggests overcorrection.  
- Ideally, $\lambda_{GC} \approx 1$.  

### QQ Plot (Quantile–Quantile Plot)
Used to visualize whether observed p-values deviate from expectation.  

- **X-axis**: expected $-\log_{10}(p)$ under the null hypothesis.  
- **Y-axis**: observed $-\log_{10}(p)$.  
- If SNPs are not associated, points should follow the diagonal line.  
- **Deviation** (systematic inflation above the line) indicates population stratification.  

#### Interpretation
- A straight line along expectation → no stratification, results are reliable.  
- Curvature upwards (observed > expected) → inflation of test statistics, many false positives.  
- Significant peaks above the line represent **true associations**, if stratification has been corrected.  


## Practical Workflow for GWAS

1. **QC Step**  
   - Check for population stratification using MDS, PCA, or related methods.  

2. **Correction**  
   - Include **population structure covariates** (e.g., top MDS or PCA components) in association tests.  
   - Apply **genomic control (λGC)** if inflation is detected.  

3. **Validation**  
   - Use QQ plots to verify that observed p-values mostly follow expectation.  
   - Ensure only a small subset of SNPs deviate significantly (the true signals).  


## Key Take-Home Messages
- Population stratification is a **major source of confounding** in GWAS.  
- It can create false associations if not corrected.  
- MDS and PCA are commonly used to detect structure.  
- Genomic control factor ($\lambda_{GC}$) and QQ plots help evaluate correction.  
- Always check for and correct stratification before interpreting GWAS results.  

