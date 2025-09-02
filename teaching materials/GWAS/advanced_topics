# Advanced Topics in GWAS

## 1. Linear Mixed Models (LMM) and Covariate Adjustment

### Why Adjust for Covariates?
In GWAS, many **non-genetic factors** can influence a phenotype:
- **Biological**: sex, age, ancestry.  
- **Technical**: study site, genotyping platform, lab batch.  
- **Environmental**: lifestyle, exposures, diet.  

If ignored, these introduce **confounding**, leading to **false-positive associations**.

### The Linear Mixed Model
The general model is:

$$
Y = Xb + Zu + \epsilon
$$

- $Y$ = phenotype vector.  
- $Xb$ = fixed effects (e.g., SNP genotype, covariates).  
- $Zu$ = random effects (population structure, kinship).  
- $\epsilon$ = residual error.  

**Why useful?**
- Corrects for hidden relatedness between individuals.  
- Reduces inflation of test statistics.  
- Maintains statistical power.  

**Example**:  
When studying metabolite levels, adjusting for **age** and **sex** ensures that SNP effects are not confounded by these factors.

## 2. GWAS Workflow

A well-designed GWAS follows these main steps:

1. **Phenotype QC**
   - Normalize quantitative traits.  
   - Define strict case/control groups.  
   - Remove outliers.  

2. **Genotype QC**
   - Exclude SNPs with low call rate (< 95%).  
   - Remove individuals with > 5% missing genotypes.  
   - Filter SNPs deviating from Hardy–Weinberg equilibrium in controls ($p < 1 \times 10^{-6}$).  

3. **Association Testing**
   - Quantitative traits → linear regression.  
   - Binary traits → logistic regression.  
   - Use LMMs to correct for stratification/relatedness.  

4. **Visualization**
   - **QQ plot**: observed vs expected p-values.  
   - **λGC (genomic control factor)**: inflation indicator (ideal ≈ 1).  
   - **Manhattan plot**: genome-wide association map.  

5. **Multiple Testing Correction**
   - Bonferroni correction.  
   - False Discovery Rate (FDR).  
   - Genome-wide threshold ($p < 5 \times 10^{-8}$).  

6. **Associated Markers**
   - SNPs above threshold are flagged for further validation.  

## 3. Statistical Replication

Replication is the **gold standard** to validate GWAS findings.  

- Confirms that associations are **not false positives**.  
- Demonstrates **generalizability** beyond the discovery dataset.  

### Requirements
- Use an **independent dataset**.  
- Apply the same phenotype definition.  
- Ensure adequate sample size to replicate the effect.  

### Extended Applications
- **Ethnic-specific effects**: test across populations with different ancestry.  
- **Generalization**: replication across diverse cohorts shows broad biological relevance.  

## 4. Meta-GWAS (Meta-Analysis)

### Concept
Instead of pooling raw individuals, combine **summary statistics** from multiple GWAS studies.  

### Requirements
- All studies must analyze the **same phenotype**.  
- Standardized QC procedures.  
- Independent sample sets (to avoid overlap).  

### Advantages
- Increases power to detect small-effect SNPs.  
- Enables study of rare phenotypes.  
- Avoids data-sharing restrictions.  

## 5. Data Imputation

### Why Impute?
- SNP chips cover only part of the genome.  
- Imputation predicts untyped genotypes using **reference panels** (HapMap, 1000 Genomes, UK Biobank).  

### How It Works
- Relies on **linkage disequilibrium (LD)**: nearby SNPs are correlated.  
- Missing SNPs can be inferred based on haplotypes.  

### Benefits
- Improves SNP density without additional genotyping costs.  
- Harmonizes datasets across different genotyping platforms.  
- Increases the chance of finding true associations.  

**Example**:  
If SNP A and SNP B are strongly correlated, and only SNP A is genotyped, imputation can predict SNP B’s genotype with high accuracy.

## 6. Quality Control (QC) in GWAS

QC ensures that results are not driven by artifacts.  

### Pre-QC
- Sample quality: remove individuals with excessive missing genotypes.  
- Sex check: confirm reported vs genetic sex.  
- Heterozygosity: exclude extreme outliers.  

### Marker QC
- **MAF**: exclude rare SNPs (< 1%).  
- **Call rate**: filter poorly genotyped SNPs.  
- **Hardy–Weinberg equilibrium**: test in controls.  

### Post-QC
- Recompute principal components (population structure).  
- Prepare dataset for imputation.  
- Ensure consistency across datasets before meta-analysis.  

## 7. Visualization and Statistical Checks

### QQ Plot
- Compares observed vs expected p-values.  
- Straight line → well-calibrated test.  
- Upward deviation → inflation (often stratification or relatedness).  

### Genomic Control (λGC)
- Ratio of median observed test statistic to expected.  
- λGC > 1 → inflation (needs correction).  
- λGC ≈ 1 → no inflation.  

### Manhattan Plot
- X-axis: chromosome position.  
- Y-axis: –log10(p).  
- Peaks above threshold = significant loci.  

## 8. Key Take-Home Messages
- **LMMs** reduce confounding due to relatedness/structure.  
- **Replication** confirms findings and ensures robustness.  
- **Meta-analysis** combines studies to boost discovery power.  
- **Imputation** fills in missing SNPs for better coverage.  
- **QC is fundamental** at both the sample and marker level.  
- **Plots (QQ, Manhattan)** help detect artifacts and visualize associations.  
- GWAS = **pipeline**: QC → association → correction → visualization → replication → interpretation.  
