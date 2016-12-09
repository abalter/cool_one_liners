My awk version:

    awk -v OFS="\t" -v FS="\t" '$3=="gene" {print $1,$4,$5,$2,$3,$6,$7,$8,$9}' Homo_sapiens.GRCh38.85.gtf >Homo_sapiens.GRCh38.85.bed

Julja's perl version:

    perl -n -e 'chomp;@f=split/\t/; if($f[2] eq "gene"){ print join("\t", @f[0,3,4,8]),"\n"}' < gtffile
