## Salmon/DESeq2 DEG ranking test 

**Aim**: Rank DEGs by TPM/Count inputs and shrinkage method 

**Raw data**: [GSE157852](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE157852), 72hpi (N=3)

**Method**

1. Salmon Indexing (with Decoys): reused my [previous indexing decoys and indexing files](https://github.com/Mira0507/seqc_comparison)

2. Salmon Mapping: salmon_remap.sh

```bash
#!/bin/bash



# Define index file directory
ind=~/Documents/programming/Bioinformatics/SEQC/reference_GENCODE/salmon_index/gencode_index

# Define file names 
samples=(Mock_72hpi_S{1..3} SARS-CoV-2_72hpi_S{7..9})



for read in ${samples[*]}

do
    salmon quant -i $ind -l A --gcBias --seqBias -r ~/Documents/programming/Bioinformatics/Salmon-test/rawdata/${read}.fastq.gz -p 16 --validateMappings -o ${read}.salmon_quant
done

cd ..
```

3. DE analysis: 
