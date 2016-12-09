My awk version:

    awk -v OFS="\t" -v FS="\t" '$3=="gene" {print $1,$4,$5,$2,$3,$6,$7,$8,$9}' Homo_sapiens.GRCh38.85.gtf >Homo_sapiens.GRCh38.85.bed

Julja's perl version:

    perl -n -e 'chomp;@f=split/\t/; if($f[2] eq "gene"){ print join("\t", @f[0,3,4,8]),"\n"}' < gtffile

Julja's python version (why? I don't know):

    echo -e 'with open("/home/exacloud/lustre1/CompBio/genomic_resources/gtf/hg38/release-85/Homo_sapiens.GRCh38.85.gtf","r") as f:\n  for line in f:\n    vals = line.split("\t");\n    if len(vals)>3:\n      if vals[2]=="gene":\n        print vals[0],vals[3],vals[4],vals[8];' |python >python.bed
    
    
