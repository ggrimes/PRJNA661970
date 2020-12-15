# PRJNA661970
re-analysis of study  PRJNA661970 from paper [Pathological and molecular examinations of postmortem testis biopsies reveal SARS-CoV-2 infection in the testis and spermatogenesis damage in COVID-19 patients](https://www.nature.com/articles/s41423-020-00604-5#Sec2) using [nfcore-rnaseq version 2.0 ](https://nf-co.re/rnaseq/2.0/usage)



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
