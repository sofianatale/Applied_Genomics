# Sample Size in GWAS

## Why Sample Size Matters
In **Genome-Wide Association Studies (GWAS)**, the **sample size** is a key determinant of the **statistical power** to detect associations between genetic variants and a phenotype.  

- With too few individuals, allele frequency differences between cases and controls cannot be reliably estimated.  
- Example: if you test only 10 individuals, even if 7 are affected, the variant may still appear heterozygous or random → results are unreliable.  
- A **large sample size** provides a robust estimation of allele frequencies, ensuring that statistical tests for association are meaningful.  

## Factors Affecting Power
Power depends not only on sample size but also on:  
- The **level of significance** (genome-wide threshold, usually $p < 5 \times 10^{-8}$).  
- The **effect size** of the causal polymorphism.  
- The **frequency of the causal allele** in the population.  
- The **linkage disequilibrium (LD)** between the causal variant and the tested SNP.  
- The **coverage of the SNP panel or array** (tag SNP density).  

> On complex traits, the **effect size of any single SNP is very small**, which is why very large cohorts are required.  

## Impact of Increasing Sample Size
- Larger cohorts **increase the probability of detecting relevant genes**.  
- Over time, as sample sizes in GWAS have grown, more loci associated with phenotypes have been discovered.  
- Increasing sample size accelerates the identification of **causal and associated loci**.  

### Example
GWAS studies on **three anthropometric traits** (BMI, height, WHRadjBMI):  
- As the sample size increased from thousands to hundreds of thousands, the **number of detected loci rose sharply**.  
- For each trait, there is a **threshold sample size** above which the discovery rate of loci accelerates.  
- Risk locus discovery has **not plateaued yet**, meaning that with larger cohorts we will likely keep discovering more associations.  

## Graph: Loci vs Sample Size
The graph shows the relationship between **sample size** and the **number of significant loci** discovered in GWAS:

- **X-axis**: Sample size (log scale).  
- **Y-axis**: Number of loci identified.  
- Traits:  
  - BMI (Body Mass Index)  
  - Height  
  - WHRadjBMI (Waist-to-Hip Ratio adjusted for BMI)  

**Key takeaway**: As sample size increases into the hundreds of thousands, the number of loci identified grows steeply, especially for highly polygenic traits like height.  

## Summary
- A **high sample size** is essential in GWAS to obtain reliable allele frequency estimates and detect true associations.  
- Larger cohorts → higher power → more loci discovered.  
- For highly polygenic traits, discovery rate continues to grow with sample size, showing that much of the genetic architecture remains to be uncovered.  
