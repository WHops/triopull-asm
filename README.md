# Triopull-asm

Triopull-asm is a snakemake workflow which accepts a bam-triplet and coordinates, and creates a child trio-asm and parents single-asm of that region by pulling the reads out of them bam file, converting to fastq and invoking hifiasm. 

Note that this is only useful in simple cases where unmapped reads are unlikely. 

# Installation

Install dependencies using

```
git clone triopull-asm
cd triopull-asm

mamba env create --file workflow/triopullenv.yaml
```

# Testrun

Run a testrun on one de-novo deletion in GIAB which is included with this pipeline using the following code. For your own data, just exchange the interval and bam parameters. 

Note that the bam files must be sorted and indexed (using e.g. samtools index file.bam)

```
conda activate triopullenv

snakemake -- cores 8 --config interval='chr7:142700000-142900000' \
                                        ref_fa='example/hg38_chr7_subset.bam' \
                                        child_bam='example/HG002_subset.bam' \
                                        father_bam='example/HG003_subset.bam' \
                                        mother_bam='example/HG004_subset.bam' \
          
```



