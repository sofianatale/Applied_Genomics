# Next Generation Sequencing Data Analysis  
### A Case Study with Galaxy and mtDNA Variants

## Galaxy Platform
**Galaxy** is an open, web-based platform for accessible, reproducible, and transparent computational research.

- **Accessible** → no programming skills required (upload data, run workflows, visualize results).  
- **Reproducible** → every parameter and dependency is tracked.  
- **Transparent** → workflows, histories, and visualizations can be shared.  
- **Community-centered** → widely used (>10,000 publications) with extensive tutorials.

**Advantages**
1. Easy to use.  
2. No installation needed (web-based).  
3. Point-and-click interface.  
4. Tracks all analysis details.  
5. Large collection of tools.  
6. Popular and widely supported.  

**Interface**  
- **Left panel**: data import + tool selection.  
- **Middle panel**: results of applied tools.  
- **Right panel**: workflow history.  

Important: Always know your **data type** and **how it was generated**, otherwise results may be misleading.

## Case Study: Identification of Variants from WGS mtDNA Data

### Background
- **Mitochondrial DNA (mtDNA)** is essential for oxidative phosphorylation (ATP production).  
- mtDNA variation defines **haplotypes**, which:  
  - Distinguish breeds, strains, or species.  
  - Affect traits (growth, sperm motility, climate adaptation).  
  - In livestock, influence economically important features (e.g., milk quality).  
- The study investigates whether **mtDNA variants** impact reproductive capacity.  

## Experimental Workflow

### Sequencing Strategy
- **Amplification** of mtDNA by **long PCR** with 2 primer pairs.  
- Libraries prepared with **Ion Fragment Library Kit** + **Ion Xpress™ Template Kit**.  
- Sequenced with **Ion Torrent PGM** (single-end, ~200 bp fragments).  
- Reads aligned to the pig reference mtDNA genome (**NC_000845.1**).  
- Data submitted to **NCBI SRA** (Accession: SRP059465).  

### PCR Primer Pairs
1. **long1 F / long1 R** → amplified ~4951–13202 bp (half mtDNA).  
2. **long2 F / long2 R** → amplified ~12700–5329 bp (second half).  

Because mtDNA is **circular**, the two amplicons cover the entire genome.  
Overlap between amplicons creates **regions with doubled sequencing depth** → if ignored, could be mistaken for structural variation.  

## Key Considerations

1. **Fragment size selection**  
   - After PCR, DNA fragmented (~200 bp) and size-selected by electrophoresis.  
   - Ion Torrent instrument used to select fragments of desired length.  

2. **Potential biases**  
   - Overlapping amplicons → depth spikes at primer regions.  
   - Misinterpretation possible if experimental design is not known.  

3. **Importance of Materials & Methods**  
   - Checking how DNA was prepared and sequenced is essential before downstream analysis.  
   - Prevents false conclusions about copy number or structural variants.  

## Data Availability
- Raw reads and BAM alignment files available at **NCBI SRA**: [SRP059465](https://www.ncbi.nlm.nih.gov/sra/?term=SRP059465).  
- Contains information on:
  - Instrument (Ion Torrent PGM).  
  - Sequencing type (single-end).  
  - Number of bases generated.  

## Expected Coverage Calculation
Coverage = **Total sequenced bases / Genome size**

- Example:  
  - Total bases: ~64 Mb  
  - Genome size: 16,679 bp (pig mtDNA)  
  - **Coverage ≈ 64,000,000 / 16,679 ≈ 3835x**  

This ensures deep sequencing of mtDNA, suitable for **variant detection**.


## Summary
- **Galaxy** provides a reproducible, user-friendly platform for NGS data analysis.  
- In this case study, **long-PCR + Ion Torrent sequencing** was applied to pig mtDNA.  
- Overlapping primer pairs ensure full coverage but introduce **depth biases**.  
- Careful inspection of **experimental design** (PCR, sequencing method, read type, fragment size) is crucial before interpreting results.  
- The dataset is public (NCBI SRA: SRP059465) and suitable for testing variant calling pipelines.
