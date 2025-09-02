# Fixation Index – F-statistics ($F_{ST}$)

## Introduction
The **fixation index** ($F_{ST}$) is one of the most widely used statistics in **population genetics**.  
It quantifies the **genetic differentiation between populations**, and was originally introduced by **Sewall Wright** (and later formalized by Fisher).

- **Intuition**: $F_{ST}$ compares the level of genetic diversity **within populations** to the diversity **across the total species**.  
- If populations are genetically similar, $F_{ST}$ is low.  
- If populations are genetically distinct, $F_{ST}$ is high.

## Definition

For a given locus (or genomic window):

$$
F_{ST} = \frac{H_T - H_S}{H_T}
$$

Where:  
- $H_T$ = **total expected heterozygosity** (pooled across all populations).  
- $H_S$ = **average expected heterozygosity within populations**.  

### Expected Heterozygosity
For a biallelic SNP with allele frequencies $p$ and $q$ ($p + q = 1$):

$$
H = 2pq
$$

- $H_T$: expected heterozygosity if all populations are combined into one.  
- $H_S$: average expected heterozygosity computed separately within each population, then averaged.  

## Interpretation of $F_{ST}$

- $F_{ST} = 0$ → Populations are genetically identical (no differentiation).  
  - Same allele frequencies in all populations.  

- $F_{ST} = 1$ → Populations are completely different.  
  - Example: Population 1 fixed for allele A, population 2 fixed for allele B.  

- $0 < F_{ST} < 1$ → Populations share alleles, but with different frequencies.  
  - Example: Allele A more frequent in pop1, allele B more frequent in pop2.  

> In practice, values of $F_{ST}$ rarely approach 1.  
> - **Human populations**: typically $F_{ST} \approx 0.05–0.15$ between continents.  
> - **Domesticated animals/breeds**: higher due to artificial selection and drift.

## Estimation Strategy

### Per-SNP vs Window-based
- **Per-SNP $F_{ST}$**: computed for each variant.  
  - Very noisy because of allele frequency sampling variance.  
- **Window-based $F_{ST}$**: average across genomic windows (e.g., 50 kb, 1 Mb).  
  - Reduces noise.  
  - Highlights genomic regions under differentiation, possibly due to **selection**.  

### Linkage Disequilibrium
- Using windows accounts for **correlation among SNPs** due to LD.  
- Helps identify **regions of differentiation**, not just single SNP outliers.  

## Study Designs and Data Types

- **Genotyping approaches**:  
  - SNP arrays  
  - Whole-genome sequencing (WGS)  

- **Pool-Seq (DNA pooling)** as a cost-effective alternative:  
  - Pool equal DNA amounts from multiple individuals (equimolar).  
  - Estimate population allele frequencies from sequencing depth.  
  - Advantages: cheap, scalable.  
  - Limitations: technical error in quantification, loss of individual-level data.  

## Practical Workflow

1. **Sampling**  
   - Define populations (e.g., breeds, geographic groups).  
   - Ensure sufficient sample size per group.

2. **Genotyping / Sequencing**  
   - SNP chip or WGS.  
   - For Pool-Seq: carefully control DNA quantification before pooling.

3. **Variant Calling and Filtering**  
   - Apply quality filters: depth, missingness, minor allele frequency (MAF).  

4. **Allele Frequency Estimation**  
   - From individual genotypes or sequencing reads (depth-aware for Pool-Seq).  

5. **$F_{ST}$ Computation**  
   - Per SNP using:  
     $$
     F_{ST} = \frac{H_T - H_S}{H_T}
     $$
   - Average within windows (e.g., 1 Mb) for robust estimates.

6. **Comparisons**  
   - Pairwise population comparisons (e.g., breed vs breed).  
   - Group contrasts (e.g., black-coat breeds vs all others).  

7. **Visualization**  
   - Plot window-based $F_{ST}$ values across chromosomes.  
   - Typically in a **Manhattan-style plot**, where higher points = stronger differentiation.  

8. **Biological Interpretation**  
   - Annotate high-$F_{ST}$ regions.  
   - Link to candidate genes and pathways.  
   - Generate hypotheses about local adaptation (e.g., trypanosome resistance, coat color, altitude adaptation).  

## Notes and Considerations

- **$F_{ST}$ compares diversity between vs within populations of the same species.**  
- Important to define in advance:  
  - Number of individuals per population.  
  - Number of populations and comparisons.  
  - Platform (SNP chip vs WGS).  
  - Sequencing coverage and depth.  
  - Budget constraints.  

- **Low $F_{ST}$** does not always mean no selection:  
  - Selection on polygenic traits may leave subtle signals.  
- **High $F_{ST}$ windows** are candidates for **selective sweeps** or **local adaptation**.  

## Summary

- $F_{ST}$ is a measure of **genetic differentiation** between populations.  
- Defined as the proportional reduction in heterozygosity within subpopulations relative to the total.  
- Ranges from 0 (identical populations) to 1 (completely distinct populations).  
- Estimated per SNP, but typically averaged across **genomic windows**.  
- Useful for identifying genomic regions under **selection**, guiding biological interpretation of population history and adaptation.
