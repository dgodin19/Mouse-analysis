# Mouse-analysis
RNA sequencing analysis of "BRCA mutational status shapes the stromal microenvironment of pancreatic cancer linking CLU+ CAF expression with HSF1 signaling (KPC) (house mouse)" from the Weizmann Institute of Science. Sequencing runs from PRJNA825537, PRJNA825538, PRJNA825539 with reference genome GRCm39 refseq assembly. 

PRJNA825538 was done first, the next two will be done later. 

The general workflow for this project was: 
Build the genome index with hisat2, and index the reference with samtools. 
Generate the alignments with hisat2 and index each BAM file. 
Generate bigwig files to make it easier to look at in IGV. 
Perform feature counts analysis with featureCounts in R with the subread package. 
Perform classification based analysis with salmon in bash. 
