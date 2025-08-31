# Inbreeding and the Inbreeding Coefficient (F<sub>PED</sub>)

## Definition

The **inbreeding coefficient (F<sub>PED</sub>)** indicates the **probability (0–100%) that two alleles at a given locus in a diploid individual are identical by descent (IBD)**, i.e., inherited from a common ancestor.  

- Calculated from **pedigree information**.  
- Assumes that each gene has two forms, and each has an equal chance of being transmitted to the next generation.  
- At the **population level**, it is expressed as the average across all individuals.  

## Identical by Descent (IBD) vs. Identical by State (IBS)

- **Identical by Descent (IBD):** two alleles are copies inherited from a common ancestor.  
- **Identical by State (IBS):** two alleles are identical in sequence but cannot be traced back to the same ancestor.  

Distinguishing IBD from IBS is crucial for estimating inbreeding, since IBS may falsely inflate homozygosity unrelated to shared ancestry.

## Individual vs. Genome-wide Definitions

- **Individual level (one locus):**  
  Probability that two alleles at a locus are IBD.  

- **Genome-wide level (all loci):**  
  Equivalent to the **proportion of autozygosity** in the individual’s genome (fraction of loci homozygous due to shared ancestry).  

This genomic definition can be estimated using **genomic tools** (e.g., SNP genotyping, sequencing) instead of pedigrees.

---

## Pedigree-based Inbreeding Coefficient (F<sub>PED</sub>)

### Advantages
- Simple to compute with known genealogical trees.  
- Provides an estimation of inbreeding at the individual and population levels.  

### Limitations
1. **Founder assumption**: assumes founders of the base population are unrelated (not always true).  
2. **Pedigree completeness**: requires full paternal and maternal lineage information. Missing ancestors → underestimated inbreeding.  
3. **Registration errors**: assumes all pedigree records are correct.  
4. **Recombination**: ignores stochastic recombination events across generations.  
5. **Selection bias**: does not account for loci under selection, which deviate from Hardy–Weinberg equilibrium.  

---

## Genomic Inbreeding Estimation

Pedigree-based estimation can be complemented or replaced by **genomic data**.  
Two key approaches:

- **Runs of Homozygosity (ROH):**  
  Long stretches of homozygous genotypes indicate recent common ancestry.  

- **Genotype-based measures:**  
  Direct calculation of homozygosity from SNP chips or sequencing, without relying on pedigrees.  

---

## Inbreeding Depression

- **Inbreeding increases homozygosity** but does not change allele frequencies.  
- Leads to:
  - Reduction in genetic variability.  
  - **Excess of homozygous genotypes** and a **deficit of heterozygotes** compared to Hardy–Weinberg equilibrium expectations.  
  - Higher probability of recessive **deleterious alleles** being expressed in homozygous state.  

Statistical test:  
- Compare **observed vs. expected genotype frequencies** under Hardy–Weinberg equilibrium.  
- Use a **χ² test with 1 degree of freedom** to detect deviations.  

---

## Practical Example

- **Expected inheritance**: 25% of genome from each grandparent.  
- In reality, recombination may cause deviations (range 0–50%).  
- Pedigree-based calculations assume average transmission, while genomic estimations reveal the actual variation.  

---

## Summary Table

| Approach | Description | Advantages | Limitations |
|----------|-------------|------------|-------------|
| **F<sub>PED</sub> (Pedigree-based)** | Probability alleles are IBD based on known pedigree | Simple, widely used | Requires complete and correct pedigree; ignores recombination & selection |
| **Genomic ROH** | Detects long homozygous stretches from genomic data | Does not require pedigree; higher resolution | Requires SNP or sequencing data; costlier |
| **Population average** | Mean of individual inbreeding coefficients | Summarizes population level | Sensitive to sample bias |

---

## Key Takeaways

- **Inbreeding coefficient (F<sub>PED</sub>)** measures the probability of alleles being IBD.  
- Pedigree-based estimations are limited by data completeness, recombination, and selection.  
- **Genomic inbreeding measures** (ROH, SNP-based) provide more accurate, locus-specific estimates.  
- Inbreeding leads to **increased homozygosity**, reduction in variability, and **higher risk of deleterious recessive alleles** being expressed.  
