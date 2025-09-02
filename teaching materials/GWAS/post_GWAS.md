# Post-GWAS Analysis and Functional Interpretation

## 1. Post-GWAS Analysis

After identifying significant SNPs in a GWAS, the next step is to **interpret the biological meaning** of these associations.  
This involves connecting the statistical signals to genes, regulatory elements, and pathways.

### SNP-to-Gene Annotation
- **Goal**: find which genes are located near or within associated SNPs.  
- **Approaches**:
  - Use **GFF/GTF files**: contain genomic coordinates of genes.  
  - Overlap SNP positions with annotated genomic features.  
  - Tools such as **Biomart** or **VEP (Variant Effect Predictor)** automate this step.  

### Feature Intersection
- **Question**: do GWAS SNPs overlap with known genomic features (e.g., promoters, enhancers, regulatory elements)?  
- **Tools**:  
  - **BEDTools intersect** → screens for overlaps between SNPs and genomic features.  
  - Works with BED/GFF/VCF/BAM formats.  
  - Allows fine control over overlap definitions (partial/full).  

### Practical Example
1. GWAS peak on chr12.  
2. Identify SNP position = 123,456,789.  
3. Overlap with GFF gene annotation.  
4. Result: SNP lies near **GeneX**, a candidate gene for the phenotype.  

## 2. GWAS Catalog

The **GWAS Catalog** is a curated resource collecting published SNP–trait associations.

- Founded by NHGRI in 2008.  
- Contains results from thousands of GWAS studies.  
- Provides:
  - **Search interface** (by SNP, gene, or trait).  
  - **API access** for automated queries.  
  - **Summary statistics** (downloadable tables, harmonized datasets).  
  - **Diagrams** of SNP–trait associations mapped to the human genome.  

### Why Use It?
- To validate whether a SNP or region has been previously associated with traits.  
- To annotate new findings by comparing them with published results.  
- To generate hypotheses by linking novel SNPs to known biology.  

## 3. Functional Association Analysis

Statistical association alone does not explain biological meaning.  
The next step is to ask:  
*Are the genes near GWAS hits enriched for specific biological functions or pathways?*

### Over-Representation Analysis (ORA)
- Compares a **list of candidate genes** (from GWAS) to background genome annotations.  
- Tests whether some **biological functions/pathways** are represented **more often than expected by chance**.  
- Common tools: DAVID, Enrichr, g:Profiler, WebGestalt.  

### Workflow
1. Input: list of genes near associated SNPs.  
2. Compare against functional categories (GO terms, KEGG pathways, Reactome).  
3. Compute enrichment using statistical tests (Fisher’s exact test, hypergeometric test).  
4. Correct for multiple testing (FDR).  
5. Report significantly enriched terms.  

### Example
- Input: 20 candidate genes.  
- ORA result:  
  - Function A (e.g., lipid metabolism) → p = 0.0001 (enriched).  
  - Function B (e.g., immune response) → p = 0.001 (enriched).  
  - Function C (e.g., cell adhesion) → p = 0.301 (not significant).  

### Interpretation
- Functions A and B are **likely biological pathways** underlying the phenotype.  
- Function C is likely unrelated or not strongly supported by data.  

## 4. Key Take-Home Messages
- **Post-GWAS analysis** links SNPs to biological features using annotation and intersection tools.  
- **GWAS Catalog** is a central database to cross-reference new findings with published results.  
- **Functional association analysis (ORA)** helps identify pathways enriched in candidate genes, moving from statistical association to **biological interpretation**.  
- The integration of annotation, catalog cross-checking, and enrichment analysis is essential to **translate GWAS hits into mechanistic insights**.
