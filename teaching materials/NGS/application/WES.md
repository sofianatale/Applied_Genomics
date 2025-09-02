# Whole-Exome Sequencing (WES)

## Introduction
- **Whole-exome sequencing (WES)** = NGS method targeting the protein-coding regions of the genome.  
- Human exome = **<2% of the genome**, but contains ~85% of known disease-related variants.  
- Cost-effective alternative to **whole-genome sequencing (WGS)**.  
- Typical data: **4–5 Gb per exome vs ~90 Gb per whole human genome**.  

### Advantages
- Identifies variants across a wide range of applications.  
- Comprehensive coverage of coding regions.  
- Smaller and more manageable data sets → easier and faster analysis.  
- Broad applications: population genetics, rare genetic disease, cancer studies.  


## Hybridization Capture (Target Enrichment)
WES relies on **hybridization capture** to enrich coding regions.

**Workflow**:
1. **Library preparation**  
   - DNA fragmented (mechanical/enzymatic).  
   - Sequencing adapters added.  
   - PCR amplification may be used.  
2. **Hybridization with probes**  
   - Biotinylated probes (“baits”) hybridize to coding regions.  
   - Thousands of probes (up to 500k) target ~20,000 coding regions.  
3. **Capture with streptavidin**  
   - Bait–DNA complexes isolated.  
   - Non-target DNA washed away.  
4. **Sequencing**  
   - Only captured exonic fragments sequenced.  

**Key Point**: Probes are designed to bind specific exonic regions, allowing enrichment of the exome before sequencing.

## Applications
- **Rare variant discovery** → multiple unrelated affected individuals sequenced; shared variants prioritized.  
- **Mendelian disorders** → powerful strategy with modest sample sizes.  
- **De novo mutations** → family-based sequencing (parents unaffected, child affected).  
- **Extreme phenotypes** → sequencing individuals at opposite ends of a quantitative trait (e.g., tall vs short).  

## Variant Filtering Strategy
After WES, thousands of variants are typically identified. Filtering is necessary.

### Discrete Filtering
- **Assumption**: any allele present in a reference “filter set” (databases) is unlikely to be causative.  
- Removes common polymorphisms → focuses on novel/rare variants.  
- Only ~2% of SNVs identified by exome sequencing are novel.  
- Greatly reduces candidate genes to a small, high-priority list.  
- Exceptionally powerful for **rare Mendelian disorders**.  

### Filtering Steps
1. Identify variants shared across affected individuals.  
2. Compare against public databases (e.g., 1000 Genomes, gnomAD).  
3. Exclude common polymorphisms.  
4. Prioritize rare, novel variants with potential disease impact.  

## Comparison of Approaches

| Approach | Target | Coverage per base | Data size | Cost | Notes |
|----------|--------|-------------------|-----------|------|-------|
| **Targeted sequencing** | Specific genes/SNPs | Very high | Very small | Lowest | Focused approach, useful in clinical settings |
| **Whole-exome sequencing (WES)** | All coding regions (~2% of genome) | High | Moderate (~4–5 Gb) | Medium | Captures most disease-causing variants |
| **Whole-genome sequencing (WGS)** | Entire genome | Moderate (spread over 3 Gb) | Large (~90 Gb) | Highest | Comprehensive, unbiased |


## Summary
- WES focuses on **exons**, where most disease-related variants occur.  
- **Hybridization capture** enriches exonic DNA for sequencing.  
- Enables discovery of **rare variants** and candidate genes in Mendelian and complex diseases.  
- **Filtering strategies** (database-based, family-based, extreme phenotype comparisons) refine results.  
- Researchers can choose between **targeted panels, WES, or WGS** depending on cost, data needs, and research goals.

