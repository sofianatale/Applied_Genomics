# Genome-Wide Significance and Multiple Testing Correction in GWAS

## Introduction
In a **Genome-Wide Association Study (GWAS)**, we test **hundreds of thousands to millions of SNPs** for association with a phenotype.  

- Each SNP is tested individually with a statistical test (e.g., $\chi^2$, Fisher test, logistic regression).  
- Each test yields a **p-value**, representing the probability that the observed difference in allele frequency (between cases and controls, or across phenotypes) occurred by chance.  

### The Challenge
- If we test **1 SNP** at significance level $\alpha = 0.05$, we accept a 5% chance of false positives.  
- If we test **1,000,000 SNPs**, then by chance alone we expect:  

$$
1,000,000 \times 0.05 = 50,000 \text{ false positives}
$$

Thus, **without correction**, the majority of significant SNPs could be false signals.  

## The Need for Multiple Testing Correction
Multiple testing correction ensures that the overall false positive rate across all SNPs remains under control.  

The **goal** is to adjust the significance threshold so that only truly strong signals are retained as significant.  


## Bonferroni Correction

### Formula
$$
\alpha_{\text{Bonf}} = \frac{\alpha}{N}
$$

Where:  
- $\alpha$ = desired experiment-wide significance level (commonly 0.05)  
- $N$ = number of independent SNPs tested  

### Example
- If $\alpha = 0.05$ and $N = 150,000$:  

$$
\alpha_{\text{Bonf}} = \frac{0.05}{150,000} \approx 3.3 \times 10^{-7}
$$

- Only SNPs with $p < 3.3 \times 10^{-7}$ would be considered significant.  

### Assumptions and Limitations
- Assumes **all tests are independent**.  
- In GWAS, this is not true because SNPs are often in **linkage disequilibrium (LD)**.  
- This makes Bonferroni **overly conservative** → true associations may be missed.  

## Standard Genome-Wide Significance Threshold

Over time, empirical studies and simulations established a **widely accepted threshold**:

$$
p < 5 \times 10^{-8}
$$

- This threshold corresponds approximately to a Bonferroni correction for ~1 million independent SNPs (after accounting for LD).  
- It balances stringency and power.  
- Today, $p < 5 \times 10^{-8}$ is the **standard genome-wide significance cutoff** for SNP-trait associations.  

## False Discovery Rate (FDR)

Instead of controlling the probability of *any* false positives (FWER), **FDR controls the proportion of false discoveries among significant results**.  

### Benjamini–Hochberg Procedure
1. Rank all SNPs by p-value from smallest to largest.  
2. For each SNP $i$ out of $m$ total SNPs:  

$$
q(i) = \frac{i}{m} \cdot \alpha
$$

3. Identify the largest $i$ such that $p(i) < q(i)$.  
4. Declare SNPs with ranks $\leq i$ as significant.  

### Example
- Suppose $m = 20$ SNPs and $\alpha = 0.05$.  
- The 5th SNP in the ranking has $p = 0.01$.  
- Threshold: $q(5) = \frac{5}{20} \times 0.05 = 0.0125$.  
- Since $p(5) = 0.01 < 0.0125$, SNP #5 is significant.  

### Advantages
- Retains more true positives than Bonferroni.  
- Especially useful in polygenic traits where many SNPs have small effects.  

### Limitations
- FDR allows some false positives by design.  
- Less conservative → must be interpreted carefully.  

## Permutation-Based Correction
- Involves **reshuffling phenotype labels** across individuals many times.  
- Builds an **empirical null distribution** of test statistics while preserving LD structure.  
- P-values for each SNP are compared against this distribution.  

### Pros
- Accounts for the correlation among SNPs.  
- Provides accurate empirical p-values.  

### Cons
- Computationally **very demanding**.  
- Not feasible for large-scale GWAS with millions of SNPs.  

## Comparing Methods

| Method | Controls | Assumption | Pros | Cons |
|--------|----------|------------|------|------|
| **Bonferroni** | Family-wise error rate (FWER) | SNPs are independent | Simple, strict | Overly conservative, ignores LD |
| **Genome-wide threshold ($5 \times 10^{-8}$)** | Empirical FWER | LD-adjusted SNP count | Standard in GWAS, widely accepted | Rigid threshold |
| **FDR (Benjamini–Hochberg)** | False discovery proportion | Ranking of p-values | Higher power, flexible | Allows some false positives |
| **Permutation** | Empirical null distribution | Preserves LD | Accurate, adaptive | Too computationally heavy |

## Workflow Summary

1. **Perform SNP-level tests**  
   - Compute p-values for all SNPs.  

2. **Choose correction method**  
   - Bonferroni → conservative, safe.  
   - FDR → more discoveries, tolerates some errors.  
   - Genome-wide threshold ($5 \times 10^{-8}$) → standard in GWAS.  
   - Permutations → small datasets, research-level.  

3. **Plot results**  
   - Use a **Manhattan plot** with $-\log_{10}(p)$ on the y-axis.  
   - Significant SNPs rise above the correction threshold line.  

4. **Interpret peaks**  
   - Peaks = clusters of significant SNPs in LD.  
   - Investigate nearby genes → candidate loci for the trait.  

## Key Take-Home Messages
- In GWAS, multiple testing correction is **mandatory**.  
- **Bonferroni**: simple but conservative.  
- **$p < 5 \times 10^{-8}$**: the gold standard threshold in modern GWAS.  
- **FDR**: useful when many associations are expected, improves power.  
- **Permutation tests**: accurate but impractical for large datasets.  
- **Interpretation**: true signals appear as **peaks of SNPs in LD**, not isolated single SNPs.
