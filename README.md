# Gen711

Uploaded FASTQ files of two species, *Vigna angularis* and *Vigna radiata* from ENA using 
>1. PATH2SRA_TOOLKIT/fastq-dump --defline-seq '@$sn[_$rn]/$ri' --split-files SRR1642852
>2. PATH2SRA_TOOLKIT/fastq-dump --defline-seq '@$sn[_$rn]/$ri' --split-files SRR1980930
- After several attepts at downloading files using wget, ORP would not run unless files were grabbed using SRA_toolkit

Subsampled down reads using SeqTk
>1. seqtk sample -s100 SRR1642852_1.fastq 10000000 > new_mung_R1.fq
>2. seqtk sample -s100 SRR1642852_2.fastq 10000000 > new_mung_R2.fq
>3. seqtk sample -s100 SRR1980930_1.fastq 10000000 > new_adzuki_R1.fq
>4. seqtk sample -s100 SRR1980930_2.fastq 10000000 > new_adzuki_R2.fq
- several attempts were made using files of various sizes and subsampled to down to smaller sizes, but they were either too big or too small. 
- The mung bean files started with 19,163,991 reads
- the adzuki bean files started with 37,313,522 reads 

ORP transcriptome assembly
>1. $HOME/Oyster_River_Protocol/oyster.mk STRAND=RF SPADES2_KMER=25 MEM=120 CPU=9 READ1=adzuki_R1.fq READ2=adzuki_R2.fq RUNOUT=adzuki_bean_ORP
>2. $HOME/Oyster_River_Protocol/oyster.mk STRAND=RF SPADES2_KMER=25 MEM=120 CPU=9 READ1=mung_R1.fq READ2=mung_R2.fq RUNOUT=mung_bean_ORP

