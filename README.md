# Sequencing Data Analysis and Variant Calling

## Description

This project processes genomic sequencing data, including read alignment, variant calling (SNPs and INDELs), functional annotation, and mutation comparison across samples. The pipeline uses several bioinformatics tools such as GATK, SAMtools, BWA, Picard, SnpEff, and bcftools to analyze genomic variants from *7 sequences*: SRR14252108, SRR14252111, SRR14252112, SRR14252102, SRR14252115, SRR14252197.

To apply this project to other sequences, you just need to change the sequence names in the configuration files and relevant commands.

## Prerequisites

### Required Tools:
- *GATK* (Genome Analysis Toolkit)
- *BWA* (Burrows-Wheeler Aligner)
- *SAMtools*
- *Picard*
- *SnpEff*
- *bcftools*

### Required Python Libraries:
- *pysam*
- *pandas*

Install the Python dependencies with:

bash
pip install pysam pandas


## Pipeline

1. *Download and Preparation*: Download and index the reference genome (hg38).
2. *Cleaning*: Filtering with fastp and read repair with BBMap.
3. *Alignment*: Alignment with BWA.
4. *Variant Calling*: Using GATK Mutect2 to call somatic variants.
5. *Annotation*: Annotating variants with SnpEff.
6. *Filtering and Analysis*: Filtering variants (SNPs and INDELs), statistics with bcftools.
7. *Mutation Comparison*: Merging and filtering VCF files, comparing mutations for genes of interest (e.g., TP53, KRAS).

## Instructions

Clone the repository:

bash
git clone https://github.com/your-username/your-repository.git
cd your-repository


Run the commands for each pipeline step, including alignment, variant calling, and annotation.

### Example command to call variants:

bash
/content/gatk-4.4.0.0/gatk Mutect2   -R /content/drive/MyDrive/bioinformatics_project/hg38.fa   -I /content/drive/MyDrive/bioinformatics_project/marked_duplicates_with_RG.bam   -tumor-sample tumor_sample_name   -O /content/drive/MyDrive/bioinformatics_project/variants.vcf


## Results

The results will be saved in annotated and filtered VCF files, as well as in CSV files for further analysis.

### Example of CSV output file:

csv
CHROM, POS, GENE, REF, ALT, DP, FILTER
1, 1234567, TP53, A, G, 50, PASS
2, 2345678, KRAS, C, T, 35, PASS


## Conclusion

This pipeline allows for the analysis of sequencing data, the identification and annotation of somatic variants, and filtering of results for significant mutations. It is suited for genomic studies, particularly for cancer sample analyses.

## Authors

- *Your Name*: Lead Developer
- *Collaborator 1*: Contributor

## License

This project is licensed under the MIT License.
