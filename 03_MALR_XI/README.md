# MALR on chrXI


## Defining diagnostic FASTA sequences
```bash
mkdir -p ./fastas
cat <<EOT > ./fastas/CLIB413-chrXI-tf1.fasta
>CLIB413-chrXI-tf1
ATGGGTATTGCGAAACAGTCTTGCGACTGCTGTCGCGTTCGTCGAGTAAAGTGTGACAGGAATAAACCATGTAATCGCTG
CACTCAGCGCAATTTGAACTGCACTTATCTTCAACCGTTGAAAAAGAGAGGTCCAAAATCCATTAGAGCAGGAAGCTTAA
AAAAAATAGCGGAAGTGCAGATGGTGAGTATGAATAATAATATTATGACCGCTCCGGTGGTATGTAAGAAGGTTCCGAAA
AACCTGATTGATCAATGTTTGAGGTTGTATCATGATAACTTATATGTAATTTGGCCAATGCTTTCCTACGATGATCTTCA
CAAGCTTCTAGAAGAGAAATACGATGACTGTTGCGCCTACTGGTTTCTGGTATCCCTTTCGGCAGCTACTCTTAGCGACT
TGCAAATTGAAATAGAGTATGAGGAAGGAGTCACTTTTACTGGAGAGCAGTTATGCACTCTTTGCATGTTATCTCGGCAA
TTCTTTGACGACCTTAGTAACAGCGACATAATTCGAATCATGACATACTATTGTTTGCACCGTTGTTACGCGCAGTTTGC
GGATACGAGAACTTCATATAGACTTTCTTGTGAAGCCGTGGGCCTCATCAAGATAGCTGGATTCCATCGGGAAGAAACCT
ATGAATTCCTTCCCTTCGGTGAACAACAACTCAGAAGGAAAGTTTACTATTTACTTCTTATGACAGAGAGATATTACGCT
GTATATATTAAGTGTGTCACGAGCCTAGATACAACAATAGCGCCACCACTACCAGAGGTTGTAACAGACCCTCGTCTTTC
TCTGGAAAGCTTCCTTGAGGTGATTAGAGTTTTCACTGTACCTGGAAAGTGTTTTTATGATGCTTTGGCTACTAACTGTG
TCGATGATTCCTGCACCGAAGACTCTCTAAAAAGGATATGGAACGAACTTCATACCACATCACTTGATATAGAGCCATGG
CCTTACGGATACATCGATTTTCTGTTTTCGAGGTATTGGGTCAGGACACTAGCGTGGAAACTAGTACTTCATATGAAAGG
TATGCGGATGAATTTTCTTTCGAATACTAATAACACACATATACCAGTCAAAATTGCTAGGGACATGTTGAAAGATACGT
TCTTAACTCCGAAAAACCTGTATGATGTACATGGTCCTGGAATACCGATGAAGGCATTAGAAATAGCCGATGCGTTGGTA
GATGTTGTAAATAAGTATGATCACAATATGAAGTTGGAGGCTTGGAATATTTTGTGCGATGTATCTAAGTTCGTTTTCTC
CCTGAAACATTGCAATCATAAAATGTTTCAAAGGTTTTCAACTAAATGTCAGAGTGCTCTAATCGATTTGCCTATCTCTA
GACCACTGCGCCTAAATGATGATTCCAAAGATGAAGACGACATAATTCCTTAA
EOT

cat <<EOT > RM-chrXI-tf1.fasta
>RM-chrXI-tf1
ATGGGTATTGCGAAACAGTCTTGCGACTGCTGTCGCGTTCGTCGAGTAAAGTGTGACAGGAATAAACCATGTAATCGCTG
CACTCAGCGCAATTTGAACTGCACTTATCTTCAACCGTTGAAAAAGAGAGGTCCAAAATCCATTAGAGCAGGAAGCTTAA
AAAAAATAGCGGAAGTGCAGATGGTGAGTATGAATAATAATATTATGACCGCTCCGGTGGTATGTAAGAAGGTTCCGAAA
AACCTGATTGATCAATGTTTGAGGTTGTATCATGATAACTTATATGTAATTTGGCCAATGCTTTCCTACGATGATCTTCA
CAAGCTTCTAGAAGAGAAATACGATGACTGTTGCGCCTACTGGTTTCTGGTATCCCTTTCGGCAGCTACTCTTAGCGACT
TGCAAATTGAAATAGAGTATGAGGAAGGAGTCACTTTTACTGGAGAGCAGTTATGCACTCTTTGCATGTTATCTCGGCAA
TTCTTTGACGACCTTAGTAACAGCGACATAATTCGAATCATGACATACTATTGTTTGCACCGTTGTTACGCGCAGTTTGC
GGATACGAGAACTTCATATAGACTTTCTTGTGAAGCCGTGGGCCTCATCAAGATAGCTGGATTCCATCGGGAAGAAACCT
ATGAATTCCTTCCCTTCGGTGAACAACAACTCAGAAGGAAAGTTTACTATTTACTTCTTATGACAGAGAGATTTTACGCT
GTATATATTAAGTGTGTCACGAGCCTAGATACAACAATAGCGCCACCACTACCAGAGGTTGTAACAGACCCTCGTCTTTC
TCTGGAAAGCTTCCTTGAGGTGATTAGAGTTTTCACTGTACCTGGAAAGTGTTTTTATGATGCTTTGGCTACTAACTGTG
TCGATGATTCCTGCACCGAAGACTCTCTAAAAAGGATATGGAACGAACTTCATACCACATCACTTGATATAGAGCCATGG
TCTTACGGATACATCGATTTTCTGTTTTCGAGGCATTGGGTCAGGACACTAGCGTGGAAACTAGTACTTCATATGAAAGG
TATGCGGATGAATTTTCTTTCGAATACTAATAACACACATATACCAGTCGAAATTGCTAGAGACATGTTGGGAGACACGT
TTTTAACTCCGAAAAACCTGTATGATGTACATGGTCCTGGAATACCAATGAAATCATTGGAAGTAGCCAATGCATTGGTA
GATATCGTAAATAAGTATGATCACAATATGAAGTTGGAGGCTTGGAATATTTTGTGCGATGTATCCAAGTTCGTTTTCTC
CCTGAAACATTGCAATCATAAAATGTTTCAAAGGTTTTCAACTAAATGTCAGAGTGCTCTAATCGATTTGCCTATCTCTA
GACCACTGCGCCTAAATGATGATTCCAAAGATGAAGTCGACATTATTCCCTAA
EOT
```




## Call Genotypes
```bash
source ../src/fun.sh
call_genos 'BY'         'RM'        'chrXI' 'SRR9330837'
call_genos 'RM'         'YPS163'    'chrXI' 'SRR9330810'
call_genos 'CLIB413'    'YJM145'    'chrXI' 'SRR9330813'
call_genos 'CLIB413'    'YJM978'    'chrXI' 'SRR9330815'
```


## Call Phenotyoes
```bash
source ../src/fun.sh
call_phenos 'BY'        'RM'        'SRR9330837'    'RM-chrXI-tf1.fasta'
call_phenos 'RM'        'YPS163'    'SRR9330810'    'RM-chrXI-tf1.fasta'
call_phenos 'CLIB413'   'YJM145'    'SRR9330813'    'CLIB413-chrXI-tf1.fasta'
call_phenos 'CLIB413'   'YJM978'    'SRR9330815'    'CLIB413-chrXI-tf1.fasta'
```

## Association testing
```bash
source ../src/fun.sh
qtl_map 'BY'        'RM'        'RM-chrXI-tf1.fasta'        'chrXI'
qtl_map 'RM'        'YPS163'    'RM-chrXI-tf1.fasta'        'chrXI'
qtl_map 'CLIB413'   'YJM145'    'CLIB413-chrXI-tf1.fasta'   'chrXI'
qtl_map 'CLIB413'   'YJM978'    'CLIB413-chrXI-tf1.fasta'   'chrXI'
```


## Plotting
```bash
source ../src/fun.sh
plot_association 'BY'        'RM'        'RM-chrXI-tf1.fasta'        'chrXI'
plot_association 'RM'        'YPS163'    'RM-chrXI-tf1.fasta'        'chrXI'
plot_association 'CLIB413'   'YJM145'    'CLIB413-chrXI-tf1.fasta'   'chrXI'
plot_association 'CLIB413'   'YJM978'    'CLIB413-chrXI-tf1.fasta'   'chrXI'
```


## Upload to onedrive
```bash
module load rclone
rclone copy --max-depth 1 --include "*.pdf" ./plots nihonedrive:/Data/pacbio_genomes/03_MALR_chrXI/
```
