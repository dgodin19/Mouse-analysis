# Mouse-analysis

RNA sequencing analysis of **"[BRCA mutational status shapes the stromal microenvironment of pancreatic cancer linking CLU+ CAF expression with HSF1 signaling (KPC) (house mouse)](https://pmc.ncbi.nlm.nih.gov/articles/PMC9622893/)"** from the Weizmann Institute of Science. Sequencing runs were sourced from **PRJNA825537**, **PRJNA825538**, and **PRJNA825539**, using the GRCm39 RefSeq assembly as the reference genome. Reference files were downloaded via the NCBI datasets command-line tool and reads were downloaded from the SRA.

## Motivation

This project stems from my experience working as a scribe for a breast surgeon. Inspired by the skills I acquired from the **Biostars Handbook**, I explored the Sequence Read Archive (SRA) and searched for "BRCA". Among the results, this mouse study stood out. While working with the human genome might have been computationally intensive for my system, I found this mouse study to be a manageable and meaningful entry point into RNA sequencing analysis. Moreover, cancer research commonly employs mouse models, making this project a great way to integrate my background with new skills.

### Initial Focus

The analysis began with **PRJNA825538**, with plans to analyze the other two datasets (**PRJNA825537** and **PRJNA825539**) later.

---

## Workflow Overview

The general workflow for this project included the following steps:

1. **Build Genome Index:**
   - Use `hisat2` to build the genome index.
   - Index the reference genome using `samtools`.

2. **Alignment and Indexing:**
   - Generate alignments with `hisat2`.
   - Index the resulting BAM files.

3. **BigWig File Generation:**
   - Convert BAM files to BigWig format for easier visualization in IGV.

4. **Feature Counts Analysis:**
   - Use `featureCounts` from the `subread` R package to analyze read counts.

5. **Classification-Based Quantification:**
   - Perform quantification using `salmon` in a Bash environment.

6. **Differential Expression Analysis:**
   - Conduct differential expression analysis using:
     - Feature counts output.
     - Salmon classification output.
   - Generate heatmaps for both analyses to compare results.

---

## Current Progress

For **PRJNA825538**, the design matrix was as follows:

| Sample         | Condition    |
|----------------|--------------|
| `control_1`    | `control`    |
| `control_2`    | `control`    |
| `control_3`    | `control`    |
| `knockdown_1`  | `knockdown`  |
| `knockdown_2`  | `knockdown`  |
| `knockdown_3`  | `knockdown`  |

---

This project not only allowed me to practice RNA sequencing analysis but also provided valuable insights into how cancer-related research is conducted using mouse models. The methods and outputs have enhanced my understanding of differential expression and bioinformatics workflows.

knockdown_3,knockdown


