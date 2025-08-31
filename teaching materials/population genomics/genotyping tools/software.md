# Use of Software for Population Genomic Analysis (PLINK)

## 1. Required Input Data

To run PLINK, you need **genotype data** and related information.  

### Text-based input files
- **Pedigree file (`.ped`)** → genotypes and individual/phenotype information  
- **Map file (`.map`)** → information about DNA markers  

### Compressed binary files
- **Fam file (`.fam`)** → info about individuals (phenotype)  
- **Bim file (`.bim`)** → info about marker positions  
- **Bed file (`.bed`)** → genotype information  

Binary files (`fam`, `bim`, `bed`) are often preferred for large datasets due to efficiency.

## 2. Pedigree Chart

Pedigree charts represent **relationships between individuals** in a population:  
- Squares = males, circles = females  
- Shaded = affected individuals, empty = unaffected  
- Additional symbols may indicate carriers, consanguinity, twins, or unknown sex  

Such charts are useful when studying **hereditary diseases**.

## 3. Pedigree File (`.ped`)

A **PED file** is a whitespace-delimited text file.  

The first 6 columns are mandatory:  
1. Family ID  
2. Individual ID  
3. Paternal ID  
4. Maternal ID  
5. Sex (1 = male, 2 = female, 0 = unknown)  
6. Phenotype (quantitative trait or affection status; -9 = missing)  

From column 7 onwards → genotype data (two columns per SNP to represent diploidy).  

**Example:**  
If you have 2 SNPs, the file must contain:  [6 mandatory columns] + [2 × number of SNPs] = 6 + 4 columns

## 4. Constructing a PED File

- Each **row = one individual**.  
- Each **column = one feature** (ID, sex, phenotype, or genotype).  
- Example for 1 family with 4 individuals → at least 4 rows.  
- Genotypes are listed as **pairs of alleles** (e.g., `A G`, `T C`).  

Always check consistency:
- If individual 1 is `TT` and individual 2 is `AT`, then child (individual 3) **cannot** have `AA`.  
- Missing phenotype → coded as `-9`.  

## 5. MAP File (`.map`)

The MAP file describes DNA markers. It contains **4 columns**:
1. Chromosome number  
2. Marker identifier (e.g., dbSNP ID or custom label)  
3. Genetic distance (optional, can be skipped)  
4. Base-pair position  

This allows markers to be positioned within the reference genome.

## 6. Practical Notes

- If parental information is missing → use PLINK option `--no-parents`.  
- Always document **metadata** about individuals (sex, parents, phenotypes).  
- Missing data must follow PLINK conventions (`-9` for phenotype, `0` for missing parent).  
- Pedigree format used by PLINK is **standardized** and can be used by other tools.  

## 7. Summary

- **.ped** → individuals, phenotypes, and genotypes (text format).  
- **.map** → marker coordinates.  
- **.fam / .bim / .bed** → compressed equivalents (binary PLINK format).  
- Pedigree files allow integration of **genetic and phenotypic information**, essential for population studies.  
- Always validate genotype/phenotype consistency and handle missing data carefully.  

