# OYP
Oyster River Protocol workflow and scripts (assuming paired end data)


**Trim reads in trim_galore**

```bash
trim_galore --paired {fastq1} {fastq2} -q 2
```

***Correct reads with rcorrector***

```bash
perl run_rcorrector.pl  -k 31 -t 30 -1 {trimmed_fastq1} -2 {trimmed_fastq2}

```

***Assemble in Trinity***

```
Trinity  --seqType fq --left {corrected_fastq1} --right {corrected_fastq2} --max_memory 100G --CPU 23 --output trinity_anahita --no_normalize_reads
```

*** Get coding sequences using transdecoder***

```
TransDecoder.LongOrfs -t Trinity.fasta  -m 30
```

**Note:** It is also advisable to blast the entire assembly against nr database and remove contaminant transcripts, scripts for this will follow
