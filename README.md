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
   - Generate heatmaps for both analyses to compare results. Differential expression done using DESeq. 

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

## Heatmaps for PRJNA825538
### Feature counts differential expression heatmap
![Heatmap for feature counts](featureresultsPRJNA825538/FeaturecountsHeatmap-1.png)
### Classification based differential expression heatmap
![Heatmap for classification based method](classificationresultsPRJNA825538/classification_heatmap-1.png)
### Analysis of heatmaps
So, what is going on here? From both heatmaps, it looks like there are a few spots of overlapping expression and intersample variability between biological replicates of the same condition. Filtering through the [classification deseq output](classificationresultsPRJNA825538/classification_method.csv) for transcripts with the highest variance, we find that that these transcripts are: 
| Transcript ID        | Variance  |
|-----------------------|-----------|
| NM_026147.7          | 996,741   |
| NM_008143.3          | 987,546   |
| NM_018796.3          | 974,413   |
| NM_010106.2          | 972,281   |
| NM_001410067.1       | 967,635   |
| NM_011508.2          | 917,940   |
| NM_001419058.1       | 897,330   |
| NM_007687.5          | 866,396   |
| NM_008774.3          | 851,382   |
| NM_016959.4          | 841,634   |

Filtering through the [feature counts deseq output](featureresultsPRJNA825538/differential_expression_results.csv), we find that the genes with the highest variance are: 
| Gene    | Control Variance    |  
|---------|---------------------|
| Hsdl1   | 9.67926e-05         |
| Rnf6    | 8.89335e-05         |
| Lonrf3  | 7.61594e-05         |
| St7     | 7.44192e-05         |
| Dnajc13 | 7.2517e-05          |
| Rilpl2  | 7.24769e-05         |
| Cdk16   | 6.60855e-05         |
| Ndufb9  | 6.1521e-05          |
| Pola2   | 5.63509e-05         |
| Mlph    | 5.46395e-06         |

| Gene    | Knockdown Variance   |
|---------|----------------------|
| Ldah    | 9.82739e-05          |
| Stk24   | 9.62228e-05          |
| Rnf7    | 9.42757e-05          |
| Ccdc25  | 8.80526e-05          |
| Rab11a  | 8.51672e-07          |
| Gnai1   | 7.80612e-05          |
| Stambpl1| 7.47716e-05          |
| Vopp1   | 7.29683e-06          |
| Rpl36al | 7.2966e-05           |
| Rab17   | 7.27788e-05          |
