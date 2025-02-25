# 🦠 SARS-Covid Genomic Analysis Pipeline

This project implements a complete workflow for analyzing blood samples from SARS-CoV-2 patients in **Bash** language. The pipeline processes paired samples to determine the viral genome sequence, assesses the coverage of the S protein gene, identifies genomic variations, determines viral strains via the Pangolin server, and constructs a phylogenetic tree.

---

## 📝 Project Description

The project performs the following tasks:
1. **Read Quality Control:**  
   - Evaluate read quality using the 'fasqc' tool.
   - Detect problems such as high nucleotide content, low-quality short reads, and contamination.

2. **Trimming:**  
   - Remove low-quality bases and adapter sequences using `fastp`.
   - Generate a report with `fasqc` and `multiqc`.

3. **Reference Indexing and Mapping:**  
   - Index the reference genome using Bowtie2.
   - Map reads to the reference and add Read Group (@RG) information.

4. **Post-Mapping Processing:**  
   - Sort and index BAM files using `samtools`.
   - Examine mapping statistics and evaluate close organisms.

5. **S-Gene Extraction and Coverage Analysis:**  
   - Extract coordinates of the S-gene from the annotation.
   - Use `bedtools` to assess the coverage of the S gene.

6. **Variant Calling and Consensus Generation:**  
   - Identify genomic variations using `freebayes`.
   - Merge VCF files and generate consensus sequences with `bcftools`.

7. **Protein Analysis:**  
   - Translate nucleotide sequences into amino acids.
   - Extract the S-gene and combine it with known S-protein sequences.
   - Run BLAST searches and perform multiple sequence alignment.
   - Identify amino acid substitutions and build a phylogenetic tree with `FastTree`.

8. **Contamination Check:**  
   - Use `kraken2` and the Pavian report for contamination analysis.

9. **Detection of Amino Acid Substitutions in the S Protein:**  
   - Extract S-protein sequence and record genomic substitutions.

---

## 🔧 Technologies & Tools

The pipeline is implemented using a variety of command-line tools and bioinformatics software, including:
- **Quality Control & Trimming:** fasqc, fastp, multiqc
- **Mapping & Post-Processing:** Bowtie2, samtools, bedtools
- **Variant Calling & Consensus:** freebayes, bcftools, bgzip, tabix, vcf-merge
- **Protein Analysis:** BLAST (blastp), makeblastdb, linsi (MAFFT), alv, FastTree
- **Contamination Analysis:** kraken2

---
