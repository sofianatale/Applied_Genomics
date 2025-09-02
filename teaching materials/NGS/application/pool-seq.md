# Pool-Seq and Targeted Sequencing

## Pool-Seq: Sequencing Pools of Individuals

### Concept
- **Pool-seq** = Whole genome sequencing of pools of individuals.  
- Provides a **cost-effective** alternative to sequencing each individual separately.  
- Allows estimation of **allele frequencies** in a population at lower cost.  

### Workflow
1. Extract DNA from each sample.  
2. Mix DNA in **equimolar quantities** (same number of genome copies per individual).  
   - Quantification done with techniques such as spectrometry.  
3. Sequence the pooled DNA.  
4. Map reads to reference genome.  
5. Call SNPs and calculate allele frequencies.  

Limitation: origin of each read (individual) is lost.  
Advantage: much cheaper while still providing accurate allele frequency estimates.

Applications
- **Detecting genetic basis of phenotypes**.  
- Example: *Genetic basis for red coloration in birds*.  
  - Compare two pools: red vs yellow canaries.  
  - Estimate allele frequencies at each variant.  
  - Identify genomic regions with large allele frequency differences → candidate genes.  
- Useful for **extreme phenotype comparison** (e.g., healthy vs diseased populations).  

### Cost Example
- Study: 56 Gbp sequenced for ~$400 (using a non-Illumina machine; Illumina would cost ~$700).  
- Shows strong cost-effectiveness for population-level studies.

## Targeted Sequencing

### Concept
- **Targeted sequencing** = focus on specific genes or regions of interest.  
- More rapid and cost-effective than sequencing entire genomes.  
- Uses **PCR amplification** or **hybridization-based capture** methods.  

### Approaches
- **PCR amplification** + Sanger sequencing → small number of regions.  
- **Ion AmpliSeq™ panels** → target hundreds of genes in one day (Ion PGM system).  
- **Ion TargetSeq™ Enrichment System** → up to ~60 Mb targeted regions (customizable).  

### Applications
- Cancer genomics.  
- Pharmacogenomics.  
- Discovery of novel variants in selected loci.  

## Amplicon Sequencing (Illumina)

- **Amplicon sequencing** = highly targeted, PCR-based enrichment of specific regions.  
- Produces **ultra-deep sequencing of PCR products (amplicons)**.  
- Benefits:
  - Detect **rare somatic mutations** (e.g., in tumor samples).  
  - Analyze **specific bacterial markers** (e.g., 16S rRNA gene for microbial taxonomy).  
- Workflow:
  - Design primers/probes for regions of interest.  
  - PCR amplification.  
  - NGS sequencing of amplicons.  

## Summary
- **Pool-Seq**:  
  - Effective for allele frequency estimation in populations.  
  - Best for studies comparing **extreme phenotypes**.  
  - Low-cost alternative to sequencing individuals separately.  

- **Targeted Sequencing**:  
  - Focus on specific regions/genes of interest.  
  - Cost-effective, customizable (PCR panels, hybrid capture).  
  - Used in cancer genomics, pharmacogenomics, metagenomics.  

- **Amplicon Sequencing**:  
  - Ultra-deep sequencing of PCR products.  
  - Powerful for rare variant detection and microbial community profiling.  
