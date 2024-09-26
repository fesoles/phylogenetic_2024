PART 0. Preparation
Create the environment, download all the tules and get ready to work

PART 1. Construct an evolutionary tree based on human mtDNA data (click here for data).  Don’t forget bootstrap support/posterior probabilities.

We nned to use full name files for create tree. So use this script:

``` bash
   for file in *.fasta; do
       base_name=$(basename "$file" .fasta)
       sed -i "s/>/>${base_name}_/" "$file"
   done
```
For join all fasta files:
``` bash
cat *.fasta > all_sequences_with_filenames.fasta
```

For alignment use mafft:
``` bash
mafft --auto --reorder all_sequences_with_filenames.fasta > aligned_output.fasta
```

For tree reconstrution use FastTree:
``` bash
FastTree -boot 1000 aligned_output.fasta > tree_file.tree
```

Dowloading tree_file.tree in Phylogeny.fr and obtain:

![tree_1_1](https://github.com/user-attachments/assets/259ce0dd-7d25-4483-9a46-bc174c2b8380)

PART 2. How old is Mitochondrial Eve

We count the number of mutations between Africans, multiply by 5000 years and divide by 2. It turns out that the age of mitochondrial eve was approximately 237,500 years. 

PART 3. Age of the most recent Neanderthal-modern human

Download the new data and run the same commands. The following picture is obtained

![phylo_tree](https://github.com/user-attachments/assets/20360b0a-cd3d-4e0c-a60b-673e810e6036)

The resulting age was approximately 450,000 years old, which is generally close to the literature data
