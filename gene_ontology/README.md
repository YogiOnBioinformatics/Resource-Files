# Gene Ontology Local Analysis files

These are files needed to run [goatools](https://github.com/tanghaibao/goatools) which allows one to run `Gene Ontology` analysis locally. 


📂 `mouse/`: 

Gene to Gene Ontology annotations for mouse. 

```
# get file, uncompress, remove the header lines

wget -O - http://current.geneontology.org/annotations/mgi.gaf.gz | gzip -d | tail -n +37 > mouse_annotations.tsv

python make_gene_to_go_association_file.py mouse/mouse_annotations.tsv mouse/gene_ontology_associations.pkl

```

`make_gene_to_go_association_file.py`: 

Simple script to convert the gene to `Gene Ontology` mapping file to a format compatiable with `goatools`. 

`mouse/gene_to_gene_ontology_mapping.txt`: 

This is the file to be used with `goatools`. 

