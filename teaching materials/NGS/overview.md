# Next-Generation Sequencing (NGS)

## Overview
Next-Generation Sequencing (NGS) is the **main technology in modern genomics**, enabling the production and analysis of massive amounts of sequencing data.  
- Essential for most applied genomics projects  
- Requires consideration of **error rates, throughput, costs, and timelines**  
- Provides **unbiased sequencing** of millions of DNA fragments simultaneously  

---

## From Sanger to NGS
- **Sanger Sequencing** (1st generation)  
  - One target DNA → one PCR → one sequencing reaction  
  - Each capillary = one “lane” → max **48 sequences/run**  
  - Targeted: sequence is known in advance (via specific primers)  
  - Expensive, low throughput  

- **Next-Generation Sequencing (NGS)**  
  - Many DNA targets sequenced **in parallel**  
  - Millions of fragments analyzed in a single run  
  - Uses **clonal PCR amplification** to boost signal detection  
  - Sequences are **unknown in advance**, identified only after computational analysis  

**Paradigm shift**:  
From *“we know what we sequence”* (Sanger) → to *“we discover what we sequenced”* (NGS).  


## Data Production
- Modern sequencers: up to **48 samples/run**  
- Run duration: ~**1.5 hours**  
- Read length: ~**1.5 kb per sample**  
- Additional time needed for **sample preparation, machine cleaning, setup**  
- DNA must be **amplified** to provide enough signal for detection  

## Cost Evolution
- **Human Genome Project (2003)** → ~$100,000,000 per genome  
- Today → **< $1,000 per genome**  
- Cost per **1 Mb DNA** (~1 million nucleotides) = **<$0.01 (10 cents)**  
- NGS has dramatically **outpaced Moore’s Law** in reducing costs  

## Experimental Design: Then vs Now
Every sequencing experiment involves three stages:  
1. **Planning**  
2. **Data Production**  
3. **Analysis**  

### Past (Sanger sequencing era)  
- **Data production** was the most expensive and limiting factor  
- Few sequences produced, long timelines, limited insights  

### Present (NGS era)  
- **Data production is cheap and fast**  
- **Planning** is crucial to optimize study design (large potential of data)  
- **Analysis** is the bottleneck → requires advanced bioinformatics  

Role of bioinformaticians: reduce analysis time, making large datasets manageable and interpretable.  
