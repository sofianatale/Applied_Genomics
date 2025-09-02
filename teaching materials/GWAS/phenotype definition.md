# Phenotype Definition in GWAS

Defining the **phenotype** is one of the most crucial steps in the design of a **Genome-Wide Association Study (GWAS)**.  
Since GWAS aims to link **genetic variants (genotypes)** to **observable traits (phenotypes)**, the accuracy of phenotype definition directly impacts the validity and power of the study.

## Categories of Phenotypes

### 1. Binary Disease / Affected Phenotypes
- Individuals are classified into two groups:  
  - **Cases** = affected individuals (diseased)  
  - **Controls** = unaffected individuals (healthy)  
- This is known as the **case–control design**.  
- Example:  
  - A GWAS for **gastric cancer** must carefully define what qualifies as “gastric cancer” (e.g., histological type, stage).  
  - Including individuals with misclassified or ambiguous diagnoses can introduce heterogeneity, decreasing the study’s power.

**Risk**: Non-specific case–control definitions can increase heterogeneity in genetic and non-genetic factors, leading to **decreased power for detection**.

### 2. Quantitative (Continuous) Phenotypes
- Traits measured on a **continuous scale**.  
- Examples:  
  - **Anthropometric traits**: body mass index (BMI), height, weight.  
  - **Biochemical traits**: lipid levels, metabolite concentrations, amino acid levels in blood.  
- Each individual has a measurable numeric value, allowing the use of **regression-based models** (often linear regression).

### 3. Semi-Quantitative Traits
- Traits that are **partially quantitative but not normally distributed**.  
- Example: symptom severity scores.  
- Require statistical models that can handle **non-Gaussian distributions** (e.g., logistic or non-parametric approaches).  
- Using the wrong model (e.g., assuming Gaussian distribution when not true) can bias results.

## Case–Control GWAS Design

In case–control studies, GWAS compares **allele frequencies** between cases and controls:

1. **SNP Panel**  
   - Genotypes are collected across the genome (hundreds of thousands to millions of SNPs).  

2. **Statistical Testing**  
   - For each SNP, test whether allele frequencies differ significantly between cases and controls.  
   - Common tests: **χ² test**, **Fisher’s exact test**, or logistic regression.  

3. **Association p-value**  
   - Each SNP receives a **p-value of association**, measuring whether the observed difference is due to chance.  

4. **Multiple Testing Correction**  
   - Millions of SNPs require corrections (Bonferroni, FDR).  
   - Genome-wide significance threshold: **p < 5 × 10⁻⁸**.  

## The Manhattan Plot

The standard visualization of GWAS results is the **Manhattan plot**:

- **X-axis** = chromosomal position of each SNP.  
- **Y-axis** = –log10(p-value).  
- Each dot = a SNP tested for association.  
- **Horizontal line** = genome-wide significance threshold.  

### Interpretation
- **Peaks of association**:  
  - A cluster of SNPs in strong **linkage disequilibrium (LD)** around the same locus.  
  - Indicates a robust genetic signal.  

- **Single isolated SNPs**:  
  - May represent **false positives** (genotyping error or random fluctuation).  
  - True GWAS signals usually form **clusters/peaks**, not isolated points.  

- **Zooming into peaks**:  
  - Inspect local **LD blocks** to determine the most strongly associated SNPs.  
  - Map nearby **genes** to identify candidates likely involved in the phenotype.  

## Example: Gastric Cancer GWAS

- **Cases**: patients with a specific, well-defined subtype of gastric cancer.  
- **Controls**: healthy individuals without cancer.  
- **GWAS goal**: detect variants with different allele frequencies between the two groups.  
- **Result**: a Manhattan plot where peaks represent SNPs linked to gastric cancer.  
- **Next step**: zoom into the peaks, analyze LD patterns, and identify nearby genes.

## Why Phenotype Definition Matters

- Poorly defined phenotypes dilute the signal → lower statistical power.  
- Misclassification of cases and controls introduces noise and false negatives.  
- Accurate definitions increase the likelihood of detecting true associations.  

In **case–control studies**, defining subtypes matters:  
- Example: certain variants may be associated with **intestinal-type gastric cancer**, but not with **diffuse-type gastric cancer**.  
- Mixing subtypes in the same GWAS reduces power and may hide true associations.

## Workflow Summary

1. Define phenotype: binary, quantitative, or semi-quantitative.  
2. Collect genotype data (SNP panel or WGS).  
3. Perform statistical tests for association.  
4. Correct for multiple testing.  
5. Visualize results in Manhattan plots.  
6. Validate signals via LD inspection and functional gene annotation.  

## Key Takeaways

- **Phenotype definition is the cornerstone of GWAS**.  
- Case–control studies test allele frequency differences between affected and unaffected individuals.  
- Quantitative traits require regression-based models; semi-quantitative traits need adapted approaches.  
- Manhattan plots summarize association results and guide interpretation.  
- Robust GWAS findings rely on clear phenotypes, solid statistics, and replication.

