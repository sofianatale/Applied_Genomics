## What does it mean to study genomics in a population?

Studying **population genomics** means analyzing genomic data from **many individuals**, not just a single sample.  
While a reference genome can be constructed from a single individual, understanding **variation, adaptation, and evolutionary processes** requires multiple genomes.

## Applications of Population Genomics

Population genomics helps advance our understanding in:

- **Evolutionary processes**  
  Mutation, genetic drift, gene flow, and natural selection shape genetic variation across genomes and populations.  

- **Population genetic parameters**  
  Adaptive evolution, effective population size, admixture, inbreeding/outbreeding depression, demography, and biogeography.  

- **Evolutionary histories & phylogenetics**  
  Resolving relationships of extant, ancient, and extinct species.  

- **Genomics of fitness & adaptation**  
  Identifying genomic basis of traits: adaptation, speciation, ecological/economic importance, disease resistance.  

- **Applied aspects**  
  Forensics, medicine, pharmacology, conservation genetics, sustainable management of resources.  

## Random Sampling, Genetic Drift, and Bottlenecks

- **Genetic Drift**  
  Random loss of alleles due to chance sampling across generations.  
  - Stronger effect in **small populations**.  
  - In large populations, drift still occurs but rarely fixes/loses alleles completely.  

- **Bottleneck Effect**  
  - A large parental population passes through a drastic reduction in size.  
  - Only a few individuals survive → their alleles disproportionately shape future generations.  
  - Results in a **shift in allele frequencies**, independent of initial variation.

**Example**: A forest fire drastically reduces population size. Surviving individuals carry alleles that become dominant in subsequent generations.

## Framework of Population Genomics Studies

1. **Sampling strategy**  
   - Collect individuals from different populations, environments, or phenotypes.  
   - Example: individuals adapted to high vs. low salt environments.

2. **Genotyping/Sequencing**  
   - Compare genomes and allele frequencies across groups.  

3. **Identify outlier loci**  
   - Detect loci under selection (natural or artificial).  
   - Outliers may show unusually high differentiation or deviations in allele frequency.  

4. **Statistical analysis**  
   - Work by windows of loci (to capture linked regions under selection).  
   - Use **segmentation and filtering** to distinguish true signals from noise.  

5. **Interpretation**  
   - Neutral loci → compute demographic parameters.  
   - Adaptive loci → test for causes (e.g., selection) and link to biodiversity conservation or evolutionary inference.  

6. **Validation**  
   - Cross-validate using independent methods (e.g., F-statistics, haplotype analysis, homozygosity/heterozygosity measures).  

## Concepts of Selection

- **Natural selection**:  
  Alleles that increase fitness become more frequent (e.g., coat color camouflage in animals).  

- **Artificial selection**:  
  Human preference drives allele frequency changes (e.g., breeding for a trait).  

- **Selective sweeps**:  
  A beneficial mutation rapidly increases in frequency, reducing variation (low heterozygosity) in the surrounding genomic region due to linkage disequilibrium.  
  - Over generations, recombination shortens the associated haplotype block but the beneficial mutation is maintained.  
  - Age of mutation can be estimated by the extent of surrounding linkage disequilibrium.  

## Summary of Library Preparation Methods for Population Genomics

| Method | Cost | Advantages | Disadvantages |
|--------|------|------------|----------------|
| **Whole genome re-sequencing** | $$$ | Full genome coverage; reconstruct haplotype space | Very costly, especially for large genomes; high computational resources |
| **Sequence capture** | $$$ | Reliable coverage of target regions; recovers adjacent regions | Expensive, especially relative to enzyme-based methods |
| **RAD-Seq** | $$ | Relatively inexpensive; reduces per-sample cost | Missing data; inability to target specific genome areas |
| **Genotyping by sequencing (GBS)** | $ | Low cost | Missing data; no targeting of specific genome areas |
| **RNA-Seq** | $$ | Relatively inexpensive; captures transcripts | Missing data from transcript abundance; allele-specific expression may bias SNP calling |
| **Genome skimming** | $$ | Inexpensive whole-genome coverage option | Individual genotype calling may be inaccurate in wild species with low LD |
| **Pool-Seq** | $ | Cost-effective for population-level allele frequency estimation | Individual genotypes not resolved |

Often, **combinations of different methods** are used depending on project goals, budget, and resolution required.

## Key Takeaways

- **Population genomics** requires data from many individuals to understand variation, adaptation, and evolutionary processes.  
- Random processes (drift, bottlenecks) and deterministic processes (selection) shape allele frequencies.  
- Outlier detection and genome-wide scans help identify adaptive loci.  
- Choice of **sequencing strategy** (WGS, RAD-Seq, RNA-Seq, Pool-Seq, etc.) depends on cost, resolution, and study design.  
