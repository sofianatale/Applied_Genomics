# Genome Annotation

## Genome Statistics and Coverage
- **Median gene length** is roughly proportional to genome size.  
- **Scaffold gap size**: when linking scaffolds, unknown sequences are represented with *N*.  
  - Example: paired-end sequencing can help estimate gap lengths.  
  - Rule: if length unknown → insert ~50 N.  
- **Genome coverage**: % of genome contained in assembly, based on size estimates (e.g. C-value).  
  - Good coverage = 90–95%.  
- **Gene coverage**: % of genes annotated in assembly.  
  - Often higher than genome coverage since repetitive, hard-to-assemble regions tend to be gene-poor.  

## Assembly Completeness: BUSCO
- **BUSCO** (*Benchmarking Universal Single-Copy Orthologs*):
  - Evaluates genome completeness by searching for conserved single-copy genes.  
  - If genes appear more than once → possible misassembly.  
- Useful for both assembly and annotation quality control.

## Genome Annotation Steps
Annotation = assigning biological roles to genomic sequences.  
Two main phases:
1. **Feature identification** (using algorithms and pipelines).  
2. **Annotation** (synthesizing data).  

### Main annotation workflow
1. Annotation of **repetitive elements (REs)**.  
2. **Structural annotation** → locating genes.  
3. **Functional annotation** → assigning functions to genes.  
4. Data submission, maintenance, updates.  

## Repetitive Elements (REs)

### Types of REs

* **Low-complexity sequences** → simple base runs (e.g., `AAAAA`).
* **Transposable elements (TEs):**

  * **Class I (Retrotransposons)** → RNA intermediates, *copy & paste*.
  * **Class II (DNA transposons)** → DNA intermediates, *cut & paste*.

### Challenges in RE annotation

* **Unclear boundaries** → repeat borders are often difficult to define.
* **Nested repeats** → repeats embedded inside other repeats.
* **High diversity of classes** → makes annotation complex and time-consuming.

### Approaches & Tools

#### 1. **Library-based (homology search)**

* **Concept:** compare the genome against curated repeat libraries.
* **Databases & Tools:**

  * **RepBase** → curated consensus sequences of repeats (commercial).
  * **Dfam** → open database with **profile HMMs** and **consensus sequences** of TEs, built from multiple sequence alignments.
  * **RepeatMasker** → masking tool that uses RepBase or Dfam as reference libraries (integrates BLAST and HMMs like NHMMer).

#### 2. **De novo discovery**

* **Concept:** identify novel repeats directly from the genome, without prior knowledge.
* **Databases & Tools:**

  * **REPET package**

    * **TEdenovo** → detects and classifies transposable elements *de novo* (self-alignment + clustering + consensus building).
    * **TEannot** → annotates repeats using de novo or external libraries.
  * **RepeatModeler** → widely used to build species-specific repeat libraries for downstream masking.
  
#### 3. **Mixed approaches**

* Combine both strategies:

  1. Generate a **species-specific library de novo** (e.g., with RepeatModeler or TEdenovo).
  2. Integrate it with **known libraries** (e.g., Dfam/RepBase).
  3. Use **RepeatMasker** or **TEannot** for final annotation and masking.

### Masking Repeats

* **Hard masking** → replace nucleotides with `N`.
* **Soft masking** → convert repeat bases to lowercase (`acgt`).
* **Why masking is important:**

  1. Prevents millions of spurious BLAST hits.
  2. Avoids false gene predictions caused by repeats.
  3. Informs downstream tools about repetitive regions.

## Gene Prediction Strategies

### Intrinsic (Ab initio)
- Relies only on genome sequence itself.  
- Uses **mathematical models** trained per genome.  
- Predicts **ORFs** (start codon → stop codon).  
- Pros: high sensitivity with enough training data.  
- Cons: lower accuracy for intron–exon boundaries.  

### Extrinsic
- Relies on **databases** of transcripts or proteins.  
- Uses homology to known genes.  
- Sources: RefSeq, UniProt, NCBI nr, RNA-seq data.  
- Pros: universally applicable.  
- Cons: risk of missing novel, species-specific genes.  

### Combiners
- Integrate **ab initio + extrinsic** approaches.  
- Examples: **AUGUSTUS** (can work in both ways).  
- Allow one type of evidence to override another if it improves prediction.  

## Prokaryote vs Eukaryote Annotation

### Prokaryotes
- Genes = long ORFs (>50 codons).  
- Low intergenic DNA.  
- No introns.  
- Easy to detect!  

### Eukaryotes
- Genes interrupted by introns.  
- High intergenic DNA (e.g., 62% in humans).  
- Complex regulatory features and UTRs.  
- Need to consider **codon bias**, **intron–exon boundaries**, **regulatory motifs**.  

## Transcript Information
- **Short-read RNA-seq**: high throughput but fragmented → harder to map accurately.  
- **Long-read RNA-seq (PacBio/Nanopore)**: captures full-length transcripts, resolves isoforms.  

## Annotation Targets
- **Protein-coding genes** (with ORFs).  
- **Non-coding RNAs (lncRNAs, snoRNAs, miRNAs)**.  
- **Pseudogenes** → annotated using paralog/ortholog homology (tools: PseudoPipe).  

## Manual Curation
- Human curators refine computational predictions.  
- Considered the **gold standard**.  
- Teams may collaborate with UniProt or nomenclature committees.  

## Output Formats

### GFF (General Feature Format)
- Tab-separated, 9 columns:
  1. Seqname (chromosome/scaffold)  
  2. Source (program or database)  
  3. Feature (gene, RNA, exon, etc.)  
  4. Start position  
  5. End position  
  6. Score  
  7. Strand (+/-)  
  8. Frame (0, 1, 2)  
  9. Attributes (e.g., gene ID, description)  

### Other formats
- **BED** → simple coordinates (chrom, start, end).  
- **GenBank, EMBL** → include both sequence + annotation.  
- **GTF** → gene transfer format (alternative to GFF).  

## Functional Annotation
- Assign names, symbols, and biological functions.  
- Methods:
  - Homology searches (BLAST, HMMER, UniProt).  
  - Domain databases (InterPro, Pfam).  
  - Gene Ontology (GO terms).  
  - Machine learning (HMMs, neural networks).  

## Data Submission
- Annotated genomes should be deposited in public databases:  
  - **NCBI GenBank**  
  - **ENA (European Nucleotide Archive)**  
- Submissions include:
  - Input (sample metadata, library prep).  
  - Output (assembly, annotation files).  
  - File formats: FASTA + GFF/GTF/BED + optional flat files.  

## Summary
Genome annotation is the process of adding biological meaning to an assembled genome.  
It involves:
- Identifying **repeats**.  
- Locating **genes** (structural annotation).  
- Assigning **functions** (functional annotation).  
- Using **intrinsic, extrinsic, or combined** prediction methods.  
- Requiring **manual curation** to achieve gold-standard annotations.  
- Submitting final data in standardized formats to public repositories.



