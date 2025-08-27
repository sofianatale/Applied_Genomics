# ChIP-Seq (Chromatin Immunoprecipitation Sequencing)

## Introduction
- **Goal**: study **protein–DNA interactions** to annotate genomic regions bound by proteins (e.g., transcription factors, histone modifications).  
- Allows identification of **promoters, enhancers, and other regulatory elements** involved in gene regulation.  

## Standard ChIP-Seq Workflow
1. **Crosslinking**  
   - Proteins are covalently crosslinked to DNA to stabilize interactions.  

2. **Fragmentation**  
   - DNA–protein complexes are fragmented (via sonication or enzymatic digestion).  
   - Ensures resolution at small binding regions.  

3. **Immunoprecipitation**  
   - Protein-specific **antibodies** capture DNA bound to the protein of interest.  

4. **DNA Extraction & Sequencing**  
   - Crosslinks reversed.  
   - DNA purified and sequenced.  

5. **Data Analysis**  
   - Reads mapped to reference genome.  
   - Binding regions identified as **peaks** (areas with high read depth).  
   - Peaks = regulatory regions bound by the protein.  


## Variants of ChIP-Seq
- **ChIP-exo** → uses exonuclease digestion instead of sonication → improves resolution of protein binding sites.  
- **ChIP-seq for histone modifications** → uses **MNase digestion** to fragment chromatin at nucleosome boundaries.  
- **DNase-seq** → relies on DNase I digestion to detect nucleosome-free regions.  
  - Identifies open chromatin (binding sites for many factors).  
  - Cannot specify which protein is bound.  
- **FAIRE-seq** (Formaldehyde-Assisted Isolation of Regulatory Elements)  
  - Identifies nucleosome-depleted regions by extracting DNA not crosslinked to nucleosomes.  


## Applications
- Mapping **transcription factor binding sites**.  
- Identifying **histone modifications** and chromatin states.  
- Annotating **regulatory regions** (promoters, enhancers).  
- Understanding **epigenetic regulation** of gene expression.  


## Output
- **Sequencing reads** aligned to the genome.  
- **Enrichment peaks** indicate protein-binding regions.  
- Peaks can be associated with **promoters or enhancers** of specific genes.  


## Summary
- ChIP-Seq is a powerful tool for detecting **protein–DNA interactions**.  
- Key steps: crosslink → fragment → immunoprecipitate → sequence → map.  
- Variants (ChIP-exo, DNase-seq, FAIRE-seq) increase resolution or detect open chromatin.  
- Data reveal **where proteins bind in the genome**, critical for understanding transcriptional regulation.
