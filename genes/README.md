📂 `ENSEMBL/`: 

`hg38`: 

`wget https://ftp.ensembl.org/pub/release-109/gff3/homo_sapiens/Homo_sapiens.GRCh38.109.gff3.gz`

`hg19`: 

`wget https://ftp.ensembl.org/pub/grch37/release-109/gff3/homo_sapiens/Homo_sapiens.GRCh37.87.gff3.gz`



📂 `GENCODE_UCSC_browser/`: 

Genes from `GENCODE` for each species using [UCSC Table Browser](https://genome.ucsc.edu/cgi-bin/hgTables) `BED` format. 

```
# use grep -v to filter out non-official chromosomes

cat {insert species}_gencode_vm23_UCSC_browser.bed | grep -v "_fix" | grep -v "_alt" | grep -v "_random" | grep -v "chrUn_"