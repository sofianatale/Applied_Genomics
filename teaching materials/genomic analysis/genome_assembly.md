# Genome Assembly

## Introduction
After sequencing, **genome assembly** is required when no reference genome is available to perform alignments.

Assembly can serve multiple purposes:
- Create a reference genome for a species that does not yet have one.
- Improve an existing reference genome.

Genome assembly is strictly related to **genome annotation**, since it is fundamental to know where reads belong in order to reconstruct the genome.  
Because **de novo genome assembly** requires high computational power, time and expert teams, researchers must evaluate in advance whether it is truly needed or if an existing reference genome can be used.

## Shotgun Methods

### Shotgun Sequencing
- DNA is extracted and fragmented to build a library.  
- Overlaps between fragments are analyzed to reconstruct long stretches of DNA.  

### Hierarchical Shotgun Sequencing
- Used in early genome projects.  
- Genome cut into large fragments (**contigs**) → inserted into **BAC libraries** (Bacterial Artificial Chromosomes).  
- Each BAC is shotgun-sequenced and assembled.  
- Individual BAC assemblies are aligned to recover the full genome.  
- **Nowadays:** replaced by direct whole-genome shotgun sequencing thanks to computational power.

## Experimental Workflow

### General steps
1. **Sample collection** → obtain representative tissues. Some can be saved for RNA-seq (useful for annotation).  
2. **DNA extraction** → decision between **long-read sequencing** (better continuity, e.g., PacBio, Nanopore) and **short-read sequencing** (higher coverage but fragmented, e.g., Illumina).  
3. **Genome assembly pipeline** → composed of 10 steps (see below).  

## Ten Steps of Genome Assembly

1. **Gather information about the target genome**  
   - Genome size, heterozygosity, repeats, ploidy.  
   - Methods to estimate size:  
     - *Flow cytometry* → provides **C-value**.  
     - *Databases* → use closely related species.  
     - *K-mer frequency distribution* → counts subsequences in reads.  

2. **Extract high-quality DNA**  
   - Long stretches (up to 20 kbp) for long-read sequencing.  
   - Short reads used for degraded/ancient DNA.  
   - Remove contaminants (mitochondrial, chloroplast, microbial DNA).  

3. **Design experimental workflow**  
   - Define experimental goals and sequencing depth (≥ 60x recommended).  
   - Choose library type (single-end, paired-end, mate-pair, PCR-free).  
   - Consider costs (PacBio vs Illumina).  
   - Choose between *de novo* and *reference-guided* assembly.  

4. **Choose sequencing technology & library preparation**  
   - **Illumina**: cheap, fast, high-throughput short reads.  
   - **PacBio/Nanopore**: expensive but long reads.  
   - **Hybrid approach**: correct long-read errors with short reads.  
   - Use additional technologies (Hi-C, BioNano) for scaffolding.  

5. **Ensure computational resources**  
   - Example: diploid genome (~1 Gb) → 96 CPUs, 1 TB RAM, 3 TB local storage, 10 TB shared.  
   - Cloud services (e.g., AWS) often required.  

6. **Assemble the genome**  
   - Preprocess reads (QC, filtering).  
   - Use algorithms (Greedy, OLC, De Bruijn graph, String graph, Hybrid).  

7. **Assembly polishing**  
   - Correct sequencing errors, improve consensus sequence.  
   - Errors can come from repeats, misoriented contigs, or sequencing artefacts.  

8. **Check assembly quality**  
   - Metrics: **assembly size**, **N50**, completeness.  
   - **N50** = contig length at which 50% of the assembly is contained in contigs of that size or longer.  

9. **Scaffolding & gap filling**  
   - Merge contigs using paired-end or mate-pair reads.  
   - Use genetic linkage maps or reference-guided scaffolding.  

10. **Genome annotation**  
   - Map genes and regulatory elements using RNA-seq and other functional data.  

## Algorithms for De Novo Assembly

- **Greedy algorithms** → iterative merging of overlapping reads; too simple for NGS.  
- **Graph theory** is introduced to solve complexity:
  - Vertices = reads/k-mers, Edges = overlaps.  
  - Types of graphs: undirected, directed, multigraph.  
  - In-degree / out-degree concepts used in Eulerian paths.  

### Overlap-Layout-Consensus (OLC)
1. Compute overlaps between reads.  
2. Build graph and create contigs.  
3. Infer consensus sequence.  
- Accurate but computationally expensive for large NGS datasets.  

### De Bruijn Graph (DBG)
- Reads decomposed into k-mers.  
- Vertices = (k–1)-mers; Edges = k-mers.  
- Efficient graph traversal reconstructs contigs.  
- Errors can cause unique erroneous k-mers; choice of k is crucial.  
- Uses **Eulerian paths** (each edge visited once).  
- Repeats lead to **branched structures**, resolved by longer libraries or paired/mate-pair reads.  

## Library Preparation Strategies

- **Paired-end reads** → sequence both ends of a fragment, useful to resolve small branches.  
- **Mate-pair reads** → circularize long fragments, sequence ends, useful for spanning repeats.  
- **Library size selection** → gel electrophoresis used to select fragment sizes.

## Assembly Polishing
- Correct sequencing errors (especially in long-read assemblies).  
- Increase local base accuracy and fix misassemblies.  

## Checking Quality
- **N50** as measure of contiguity.  
- Compare expected vs assembled genome size.  
- Use multiple rounds of sequencing if necessary.  

## Scaffolding and Reference-Guided Assembly
- **Scaffolding**: stitch contigs using paired/mate-pair info.  
- **Genetic linkage maps** can help order contigs.  
- **Reference-guided assembly**: align reads to a related genome; fast but may introduce errors if genomes differ structurally.  

## Summary
Genome assembly is a multi-step process requiring:
- Careful **experimental design**.  
- Choice of **sequencing technology**.  
- Large **computational resources**.  
- Appropriate **algorithms** (graph-based approaches).  

The final goal is to obtain a **chromosome-scale assembly**, followed by **annotation** to fully interpret the genomic content.  


