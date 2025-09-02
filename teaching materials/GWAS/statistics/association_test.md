# Association Tests in GWAS

## Introduction
The core of a **Genome-Wide Association Study (GWAS)** is the application of **association tests** between genetic variants (SNPs) and phenotypes.  

- Each SNP is tested **independently** to evaluate whether its allele frequencies (or genotypes) are associated with the phenotype of interest.  
- The choice of **statistical test** depends on the type of phenotype:  
  - **Quantitative traits** → use **Generalized Linear Models (GLM)** or linear regression.  
  - **Case/control traits** → use contingency tables, chi-square tests, or logistic regression.  

## Quantitative Traits
When the phenotype is continuous (e.g., height, BMI, cholesterol levels), we can model the relationship between **genotype and phenotype** using a **linear regression** framework.  

- **X-axis**: genotype (coded as 0, 1, 2 copies of the minor allele).  
- **Y-axis**: phenotype value.  
- The regression line indicates how the phenotype changes with the number of minor alleles.  

### Additive Model
The most widely used in GWAS.  
- Assumes the effect of carrying **two risk alleles = double the effect** of carrying one allele.  
- Genotypes are coded numerically:  
  - AA = 0  
  - AG = 1  
  - GG = 2  

If the slope of the regression line is:  
- **> 0** → the minor allele increases the phenotype.  
- **< 0** → the minor allele decreases the phenotype.  
- **= 0** → no association.  

## Case/Control Traits
When the phenotype is binary (e.g., diseased vs healthy), the test differs:  

- Use **chi-square or Fisher’s exact test** to compare allele frequencies between cases and controls.  
- Or use **logistic regression**, modeling the probability of being a case as a function of genotype.  

## Example: GLM in GWAS
Suppose we study SNP genotypes:  
- AA individuals → baseline phenotype.  
- AG individuals → phenotype increases compared to AA.  
- GG individuals → even higher phenotype value.  

This reflects an **additive genetic effect**, where each copy of the allele increases the phenotype by a predictable amount.  

## Minor Allele Frequency (MAF) and Coding
- The **minor allele** = the less frequent allele in the population.  
- Coding is based on the number of copies of the minor allele:  
  - 0 = no copies (homozygous major allele).  
  - 1 = one copy (heterozygous).  
  - 2 = two copies (homozygous minor allele).  

This coding allows regression models to estimate the effect of each additional copy of the minor allele on the phenotype.  

## Hypothesis Testing
For each SNP, we test:  

- **Null hypothesis ($H_0$)**: genotype has no effect on phenotype (slope = 0).  
- **Alternative hypothesis ($H_A$)**: genotype is associated with phenotype (slope ≠ 0).  

The test produces a **p-value**, which indicates whether the association is statistically significant.  

## Summary
- GWAS association tests depend on the phenotype type.  
- **Quantitative traits**: linear regression under an additive model.  
- **Case/control traits**: chi-square tests or logistic regression.  
- Additive coding (0, 1, 2 for minor alleles) is the most common approach.  
- The **p-value** from each test indicates whether the SNP is significantly associated with the phenotype.  
- Results are visualized in **Manhattan plots**, where associated SNPs appear as peaks.  
