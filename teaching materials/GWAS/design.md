# Design Considerations in GWAS

Genome-Wide Association Studies (GWAS) must be carefully designed to ensure valid and reproducible results. Several critical aspects need to be considered:

## 1. Phenotype Definition
- The phenotype must be **precisely defined**.  
- Example: in a gastric cancer GWAS, inclusion criteria must clearly identify affected individuals.  
- Poor definition reduces study power and may include genetically unrelated cases.

## 2. Structure of Genetic Variation
- Consider how **variants are organized** and related within the genome.  
- Patterns of **linkage disequilibrium (LD)** help determine how informative each SNP is.

## 3. Sample Size
- Required sample size depends on phenotype complexity.  
- **Complex diseases**: typically need **≥700 individuals** to achieve sufficient power.  
- **Simpler traits** (e.g., metabolite levels): may be studied with smaller cohorts (~250 individuals).

## 4. Population Structure
- Populations differ in allele frequencies.  
- **Stratification** must be controlled to avoid false associations due to ancestry rather than causal variants.

## 5. Multiple Testing and Significance Thresholds
- GWAS tests hundreds of thousands to millions of SNPs.  
- Correction for **multiple testing** (e.g., Bonferroni, FDR) is essential.  
- A commonly used genome-wide significance threshold is **p < 5 × 10⁻⁸**.

## 6. Replication
- Findings must be replicated in **independent cohorts**.  
- Replication ensures results are **robust, reproducible, and not study-specific artifacts**.

## Summary
A well-designed GWAS requires:
- Clear **phenotype definition**  
- Knowledge of **genetic structure** and LD  
- Adequate **sample size**  
- Control for **population stratification**  
- Rigorous **statistical testing**  
- **Replication** in independent datasets  

These considerations are fundamental to link genetic variants reliably to phenotypes.
