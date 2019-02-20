# AMBIC Epigenomics

This is the git repository for AMBIC Epigenomics project with Betenbaugh and Timp lab at JHU.

This repo is still being put together, so it will only contain parts of the analysis.

At the current stage, this should provide enough information for data parsing.

## Getting Started

### Prerequisites

The list of packages necessary for nanopore analysis :
```
ngmlr
samtools
htslib
nanopolish
bedtools
wigToBigWig (from UCSC toolkit)
```

The list of packages necessary for ATAC-seq analysis :
```
trim_galore
bowtie2
samtools
htslib
picard
bedtools
macs2
subread
```

### Installing

Most of these tools are available via conda or otherwise public source.

We will be uploading a script or command to download all dependencies in the near future.

## Snakemake pipeline

We are using [snakemake](https://snakemake.readthedocs.io/en/stable/) to generate reproducible and easy-to-follow pipelines.

You can either install snakemake and follow the steps to run the pipeline or directly look at the snakemake scripts to determine what commands to perform.

Note : The snakemake workflow may not work completely as we have tested the workflow in limited settings. You may have to make edits to the code to make it work.

### Preparing snakemake

To use snakemake, first modify the snakemake_config.yml file as appropriate for your environment.

Secondly, modify the nanopore_sample_info.csv and atacseq_sample_info.csv as necessary.

For nanopore sequencing data, we will start from basecalled data ; set up the data as follows :

* fastq name : [sample].fastq.gz 
* summary name : [sample].summary.txt
* move fastq and summary files to [workdir]/data/nanopore/reads
* fast5 in [workdir]/data/nanopore/reads/[sample_name]/

For ATAC-seq data :

* fastq name : [sample].fastq.gz
* move fastq files into [workdir]/data/atacseq/fastq/

### Running snakemake

To run snakemake, use the snakemake command in the root directory of this repo.
```
snakemake --cores 16
```

For running specific parts of the pipeline,
```
snakemake --cores 16 parse_nanopore
snakemake --cores 16 parse_atacseq
```
