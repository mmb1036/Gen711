# Gen711

Uploaded FASTQ files of two species, *Vigna angularis* and *Vigna radiata* from ENA using 
>PATH2SRA_TOOLKIT/fastq-dump --defline-seq '@$sn[_$rn]/$ri' --split-files SRR1642852
>PATH2SRA_TOOLKIT/fastq-dump --defline-seq '@$sn[_$rn]/$ri' --split-files SRR1980930

Subsampled down reads using SeqTk
>seqtk sample -s100 SRR1642852_1.fastq 10000000 > new_mung_R1.fq
>seqtk sample -s100 SRR1642852_2.fastq 10000000 > new_mung_R2.fq
>seqtk sample -s100 SRR1980930_1.fastq 10000000 > new_adzuki_R1.fq
>seqtk sample -s100 SRR1980930_2.fastq 10000000 > new_adzuki_R2.fq

ORP transcriptome assembly
>$HOME/Oyster_River_Protocol/oyster.mk STRAND=RF SPADES2_KMER=25 MEM=120 CPU=9 READ1=adzuki_R1.fq READ2=adzuki_R2.fq RUNOUT=adzuki_bean_ORP
>$HOME/Oyster_River_Protocol/oyster.mk STRAND=RF SPADES2_KMER=25 MEM=120 CPU=9 READ1=mung_R1.fq READ2=mung_R2.fq RUNOUT=mung_bean_ORP

