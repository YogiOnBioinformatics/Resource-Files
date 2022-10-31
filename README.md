# Resource-Files

Common resource files necessary for Computational Biology research. 

📂 `CAGE-Seq_Promoters/`: 

Files created using data in `tss/`. 

```
# get 1000 base pairs upstream in a stranded manner 
# 1000 is cutoff since it's usually considered maximum distance from TSS for promoter to begin
# sort regions 
# merge overlapping regions in a stranded manner and retain strand. 

bedtools slop -i tss/{insert species}_refTSS_v3.3_UCSC_browser.bed -g chrom_sizes/{insert species}.chrom.sizes -s -l 1000 -r 0 | bedtools sort -i - | bedtools merge -s -c 6 -o distinct > CAGE-Seq_Promoters/{insert species}_stranded_slop_1k_merged_refTSS_v3.3._UCSC_browser.bed
```

📂 `chrom_sizes/`: 

Tab-delimited text files indicating size of chromosomes per species.

📂 `genes/`: 

Genes from `GENCODE` for each species using [UCSC Table Browser](https://genome.ucsc.edu/cgi-bin/hgTables) `BED` format. 

```
# use grep -v to filter out non-official chromosomes

cat {insert species}_gencode_vm23_UCSC_browser.bed | grep -v "_fix" | grep -v "_alt" | grep -v "_random" | grep -v "chrUn_"
```

📂 `promoters/`:

```
# get promoters by flanking upstream 1000bp (strandedness enforced) and take first 6 columns 

bedtools flank -i genes/{insert species}_gencode_v41_UCSC_browser.bed -g chrom_sizes/{insert species}.chrom.sizes -l 1000 -r 0 -s  | cut -f1-6 > promoters/{insert species}_flank_1kb_gencode_v41_UCSC_browser.bed
```

📂 `tss/`: 

Contains BED files of Transcription Start Sites (TSS) for each species using [refTSS version 3.3](http://reftss.clst.riken.jp/datafiles/3.3/). 

NOTE: this includes isoforms and so, when visualizing on Genome Browser many TSS's looks like they're in the gene body themselves. 
