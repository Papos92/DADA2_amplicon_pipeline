# DADA2_amplicon_pipeline

**Licence:	GNU General Public License v3.0 (copy provided in directory)**<br />
Author:		Tom van Wijk - RIVM Bilthoven<br />

### DESCRIPTION

This pipeline is developed to analyse and compare amplicon sequencing
datasets of bacterial populations sequenced using paired-end reads
generated with illumina technology. Currently only the 16S V4 region
and Illumina paired-end data are supported.<br />

### REQUIREMENTS

-	Linux operating system. This software is developed on Linux Ubuntu 16.04<br />
	**Experiences when using different operating systems may vary.**
-	python 2.7.x
-	python libraries as listed in the import section of dada2_amplicon_pipeline.py
-	R v3.4.2 of later
-	Bioconductor v3.6 or later
-	dada 2 (R package)


### INSTALLATION

-	Clone the DADA2_amplicon_pipeline repository to the desired location on your system.<br />
	`git clone https://github.com/Papos92/DADA2_amplicon_pipeline.git`
-	Add the location of the DADA2_amplicon_pipeline directory to the PATH variable:<br />
	`export PATH=$PATH:/path/to/DADA_amplicon_pipeline`<br />
	(It is recommended to add this command to your ~/.bashrc file)
-	Create path variable DADA2_AMPLICON_HOME to the DADA2_amplicon_pipeline directory:<br />
	`export DADA2_AMPLICON_HOME=/path/to/DADA_amplicon_pipeline`<br />
	(It is recommended to add this command to your ~/.bashrc file)

### USAGE

Start the pipeline with the following command:

`dada2_amplicon_pipeline.py -i 'inputdir' -o 'outputdir' -x 'savetemp'`

-	**'inputdir':**	location of input directory. (required)<br />
			Should only contain either the uncompressed (.fastq)
			or compressed (.fastq.gz) sequence files containing the
			raw sequences of the forward and reverse reads.
			For each sample, these fastq files need to be named with
			an '_R1' or '_R2' tag respectively and  be furthermore identical.
			The data is expected to be free of primer-, barcode- and adapter sequences.
			Trimming, quality filtering and phiX filtering is performed by the pipeline.

-	**'outputdir':**	location of output directory.<br />
			Default = subdirectory in inputdir

-	**'savetemp':**	Set to true so save the temporary files and
			directories generated by the pipeline.<br />
			default = false<br />
			
**The parameters of the trimming step in dada2_classify_contigs.R
might need to be finetuned for your specific dataset, especcially the truncLen parameter,
which indicates at what position the forward and reverse reads should be trimmed
may vary based on the size of the target region, and sequencing tech used.**
