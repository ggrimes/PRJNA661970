# PRJNA661970

re-analysis of study  [PRJNA661970](https://www.ncbi.nlm.nih.gov/sra/SRX9086401[accn]) from paper [Pathological and molecular examinations of postmortem testis biopsies reveal SARS-CoV-2 infection in the testis and spermatogenesis damage in COVID-19 patients](https://www.nature.com/articles/s41423-020-00604-5#Sec2) using [nfcore-rnaseq version 2.0 ](https://nf-co.re/rnaseq/2.0/usage)

## Data

### SRX9086401: RNA-Seq of COVID-19 patient: adult male testis

1 ILLUMINA (Illumina NovaSeq 6000) run: 23.5M spots, 7G bases, 2.2Gb downloads


### Design 

RNA was used from each sample to prepare RNA sequencing library using Ribo-off rRNA Depletion Kit (Human/Mouse/Rat) (Cat. MRZG12324, Illumina) and KC-DigitalTM Stranded mRNA Library Prep Kit for Illumina (Cat. DR08502, Wuhan Seqhealth Co., Ltd. China) following the manufacturers instruction. The kit eliminates duplication bias in PCR and sequencing steps, by using a unique molecular identifier (UMI) of 8 random bases to label the pre-amplified cDNA molecules. The library products corresponding to 200-500 bps were enriched and quantified.

### Submitted by: Huazhong University of Science and Technology


## From Paper

To investigate the molecular changes associated with SARS-CoV-2 infection in testes, we extracted total RNA from control (controls 1, 2, and 3) and COVID-19 patient (patients 1, 2, and 3) testes and performed RNA-seq to analyze transcriptome changes. The analysis revealed 28,801 expressed coding RNAs and lncRNAs in control and COVID-19 patient testes (Supplementary Table S3), of which 2645 were upregulated and 2789 were downregulated in COVID-19 patients compared with controls (fold change > 2, FDR < 0.001) (Fig. 1k, Supplementary Fig. S4a and Table S4). These results suggest that SARS-CoV-2 infection triggers dynamic transcriptome alterations at the molecular level in testes during specific biological processes.

To further characterize changes in the transcriptome upon SARS-CoV-2 infection in the testes, we performed Gene Ontology term analysis of the differentially regulated genes. Consistent with our virus RNA detection and IHC results, the upregulated transcripts were significantly enriched in terms related to virus invasion, such as “viral gene expression” and “viral life cycle” (Supplementary Fig. S4b). Importantly, some inflammation-related processes were activated, including the “interleukin-6-mediated signaling pathway” and “regulation of B-cell proliferation”. Consistent with our histological results (Fig. 1a), the downregulated genes were significantly enriched in “spermatogenesis” and “reproduction” (Supplementary Fig. S4c), further illustrating the impact of SARS-CoV-2 infection on male fertility. Moreover, we found 32 inflammatory cytokines to be considerably upregulated, with a P value < 0.05 and fold change > 2, in COVID-19 patient testes, and 10 of these cytokines (CMTM6, FAM3C, INHBA, IL33, TNFSF10, NAMPT, CMTM4, CCL28, IL2, and TIMP1) were significantly upregulated with an FDR < 0.001 (Supplementary Fig. S4d). These bioinformatics data suggest that SARS-CoV-2 infection may lead to dysfunction of the genes that regulate spermatogenesis and inflammation-related pathways, thereby causing inflammatory immune attack in the testes and defects in spermatogenesis.

```
module load singularity
export NXF_SINGULARITY_CACHEDIR=${cachedir}
nextflow run nf-core/rnaseq --public_data_ids sra_ids --genome GRCh38 -profile singularity

sed -e 's/unstranded/reverse/g' results/public_data/samplesheet.csv > samplesheet.csv

module load singularity
export NXF_SINGULARITY_CACHEDIR=${cachedir}
nextflow run nf-core/rnaseq \
--input samplesheet.csv \
--genome GRCh38 \
--save_reference \
--skip_alignment \
-profile singularity
```
