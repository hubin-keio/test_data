# Genome download

### 1. Get metadata 

#### 1B. Bacillus cereus

```
$esearch -db assembly -query "Bacillus cereus [ORGN]" | efetch -format docsum > Bc.xml

$ cat Bc.xml | xtract -pattern DocumentSummary -element FtpPath_RefSeq AssemblyStatus SpeciesName Sub_value | grep "Complete Genome" | sed 's/ /_/g'  > Bc_comp_genomes.txt

$ shuf -n 7 Bc_comp_genomes.txt > Bc_random_seven.txtls
    
$ awk -F'\t' '{print "wget "$1"/*[1-2]_genomic.fna.gz" " -O " $3"_"$4".fna.gz"}' Bc_random_seven.txt | sed 's/Bacillus /B_/g' > Bc_dload.sh

```

### 1C. Bacillus anthracis

```
$ esearch -db assembly -query "Bacillus anthracis [ORGN]" | efetch -format docsum > Ba.xml

$ cat Ba.xml | xtract -pattern DocumentSummary -element FtpPath_RefSeq AssemblyStatus SpeciesName Sub_value | grep "Complete Genome" | sed 's/ /_/g' > Ba_comp_genomes.txt 

$ shuf -n 7 Ba_comp_genomes.txt > Ba_random_seven.txt

$ awk -F'\t' '{print "wget "$1"/*[1-2]_genomic.fna.gz" " -O " $3"_"$4".fna.gz"}' Ba_random_seven.txt | sed 's/Bacillus /B_/g' > Ba_dload.sh
```

### 1D. Bacillus thuringiensis

```
$esearch -db assembly -query "Bacillus thuringiensis [ORGN]" | efetch -format docsum > Bt.xml

$ cat Bt.xml | xtract -pattern DocumentSummary -element FtpPath_RefSeq AssemblyStatus SpeciesName Sub_value | grep "Complete Genome" | sed 's/ /_/g' > Bt_comp_genomes.txt

$ shuf -n 7 Bt_comp_genomes.txt > Bt_random_seven.txt

$ awk -F'\t' '{print "wget "$1"/*[1-2]_genomic.fna.gz" " -O " $3"_"$4".fna.gz"}' Bt_random_seven.txt | sed 's/Bacillus /B_/g' > Bt_dload.sh
```