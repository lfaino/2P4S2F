# To access the remote PC

```bash
ssh <user name>@79.49.53.20
```
```bash
ssh <user name>@10.144.91.192
```

## To remove a file

```bash
rm <name file>
```


## To copy a file to a folder

```bash
cp /home/summerschool/summerschoolFolder/testData/fusariumCREA/14_2.fq.gz  /home/summerschool/summerschoolFolder/<your foler name>
```

## To enter the folder where the data are

```bash
cd /home/summerschool/summerschoolFolder
```

or 

if you are in 

```text
summerschool@zeuspv:$~/
```


```bash
cd summerschoolFolder
```

```bash
cd /home/summerschool/summerschoolFolder --> cd ~/summerschoolFolder
```

## To modify a file in bash, you can use

```bash
nano <file name>
```

## The first sbatch file we made lok like this

```text
#!/bin/bash
# the name of your job
#SBATCH --job-name=mvila

# this is the file your ourput and errors go to
#SBATCH --output=/mvila.output.txt
#SBATCH --error=/mvila.error.txt
# 20 min, this is the MAX time your job will run
#SBATCH --time=20:00
# your work directory
##SBATCH --workdir=/scratch/nauid
# change this ater you determine your process is sane

echo "Sleeping fof 30 seconds..."
sleep 30
echo $SLURMD_NODENAME
echo "All refreshed now!"
```
# SHORT READS

## SBATCH file for fastqc

```text
#!/bin/bash
# the name of your job
#SBATCH --job-name=<job name>

# this is the file your ourput and errors go to
#SBATCH --output=<./output.FQC.txt>
#SBATCH --error=<./error.FQC.txt>
#SBATCH --qos=phyto

/home/summerschool/anaconda3/envs/summerschool/bin/fastqc \
-o /home/summerschool/summerschoolFolder/<your folder name>/   \
/home/summerschool/summerschoolFolder/testData/fusariumCREA/14_2.fq.gz
```
## SBATCH file for trimmomatic

```text
#!/bin/bash
# the name of your job
#SBATCH --job-name=<job name>
#SBATCH --cpus-per-task=16
# this is the file your ourput and errors go to
#SBATCH --output=./output.<specific analysis name>.txt
#SBATCH --error=./error.<specific analysis name>.txt
#SBATCH --qos=phyto

/home/summerschool/anaconda3/envs/summerschool/bin/trimmomatic PE -threads 16 -phred33 \
/home/summerschool/summerschoolFolder/<name your folder>/<input file>.1.fastq.gz \
/home/summerschool/summerschoolFolder/<name your folder>/<input file>.2.fastq.gz \
/home/summerschool/summerschoolFolder/<name your folder>/<name your file>_1_paired.fq.gz \
/home/summerschool/summerschoolFolder/<name your folder>/<name your file>_1_unpaired.fq.gz \
/home/summerschool/summerschoolFolder/<name your folder>/<name your file>_2_paired.fq.gz \
/home/summerschool/summerschoolFolder/<name your folder>/<name your file>_2_unpaired.fq.gz \
ILLUMINACLIP:/home/summerschool/anaconda3/envs/summerschool/share/trimmomatic-0.39-2/adapters/TruSeq3-PE.fa:2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW:4:15 MINLEN:50
```
## SBATCH file for flash

```text
#!/bin/bash
# the name of your job
#SBATCH --job-name=<job name>
#SBATCH --cpus-per-task=16
# this is the file your ourput and errors go to
#SBATCH --output=./output.<specific analysis name>.txt
#SBATCH --error=./error.<specific analysis name>.txt
#SBATCH --qos=phyto

/home/summerschool/anaconda3/envs/summerschool/bin/flash -t 16   <reads1.fastq.gz> <reads2.fastq.gz>
```

## SBATCH file for spades

```text
#!/bin/bash
# the name of your job
#SBATCH --job-name=<job name>
#SBATCH --cpus-per-task=16
# this is the file your ourput and errors go to
#SBATCH --output=./output.<specific analysis name>.txt
#SBATCH --error=./error.<specific analysis name>.txt
#SBATCH --qos=phyto

/usr/bin/spades -o <folder name> -t 16 -1 <reads1.fastq.gz> -2 <reads2.fastq.gz>
```

## SBATCH file for NanoPlot

```text
#!/bin/bash
# the name of your job
#SBATCH --job-name=<job name>
#SBATCH --cpus-per-task=16
# this is the file your ourput and errors go to
#SBATCH --output=./output.<specific analysis name>.txt
#SBATCH --error=./error.<specific analysis name>.txt
#SBATCH --qos=phyto

/home/summerschool/anaconda3/envs/nanoplot/bin/NanoPlot -o <folder name> -t 16 --fastq <reads1.fastq.gz>
```
# path for the reads to use
```text
/home/summerschool/summerschoolFolder/testData
```

## SBATCH file for hifiasm

```text
#!/bin/bash
# the name of your job
#SBATCH --job-name=<job name>
#SBATCH --cpus-per-task=16
# this is the file your ourput and errors go to
#SBATCH --output=./output.<specific analysis name>.txt
#SBATCH --error=./error.<specific analysis name>.txt
#SBATCH --qos=phyto

/home/summerschool/anaconda3/envs/summerschool/bin/hifiasm -o <output name> -t16 --ont  <reads1.fastq.gz>
```
## SBATCH file for canu

```text
#!/bin/bash
# the name of your job
#SBATCH --job-name=<job name>
#SBATCH --cpus-per-task=16
# this is the file your ourput and errors go to
#SBATCH --output=./output.<specific analysis name>.txt
#SBATCH --error=./error.<specific analysis name>.txt
#SBATCH --qos=phyto
/home/summerschool/anaconda3/bin/canu -p <assembly-prefix> -d <assembly-directory> genomeSize=<number>[g|m|k] -nanopore-raw  *fastq

```

## SBATCH file for verkko

```text
#!/bin/bash
# the name of your job
#SBATCH --job-name=<job name>
#SBATCH --cpus-per-task=16
# this is the file your ourput and errors go to
#SBATCH --output=./output.<specific analysis name>.txt
#SBATCH --error=./error.<specific analysis name>.txt
#SBATCH --qos=phyto

/home/summerschool/anaconda3/envs/verkko/bin/verkko --grid -d <output folder name> --hifi <nanopore reads fastq>
```

## SBATCH file for flye

```text
#!/bin/bash
# the name of your job
#SBATCH --job-name=<job name>
#SBATCH --cpus-per-task=16
# this is the file your ourput and errors go to
#SBATCH --output=./output.<specific analysis name>.txt
#SBATCH --error=./error.<specific analysis name>.txt
#SBATCH --qos=phyto

/home/summerschool/anaconda3/bin/flye --threads 16 --out-dir <folder name> --nano-raw <corrected reads fastq>
```


## SBATCH file for masurca

```text
#!/bin/bash
# the name of your job
#SBATCH --job-name=<job name>
#SBATCH --cpus-per-task=32
# this is the file your ourput and errors go to
#SBATCH --output=./output.<specific analysis name>.txt
#SBATCH --error=./error.<specific analysis name>.txt
#SBATCH --qos=phyto

/home/summerschool/anaconda3/envs/summerschool/bin/masurca -t 32 -i </path_to/pe_R1.fa,/path_to/pe_R2.fa> -r </path_to/nanopore.fastq.gz>
```


## SBATCH file for quast

```text
#!/bin/bash
# the name of your job
#SBATCH --job-name=<job name>
#SBATCH --cpus-per-task=3
# this is the file your ourput and errors go to
#SBATCH --output=./output.<specific analysis name>.txt
#SBATCH --error=./error.<specific analysis name>.txt
#SBATCH --qos=phyto

/home/summerschool/anaconda3/envs/quast/bin/quast.py -s -o <output name folder> -t3 <genome 1 fasta> <genome 2 fasta> <genome N fasta>
```
## SBATCH file for bwa index

```text
#!/bin/bash
# the name of your job
#SBATCH --job-name=<job name>
#SBATCH --cpus-per-task=16
# this is the file your ourput and errors go to
#SBATCH --output=./output.<specific analysis name>.txt
#SBATCH --error=./error.<specific analysis name>.txt
#SBATCH --qos=phyto

/home/summerschool/anaconda3/envs/summerschool/bin/bwa index <genome sequence>
```

## SBATCH file for bwa mem

```text
#!/bin/bash
# the name of your job
#SBATCH --job-name=<job name>
#SBATCH --cpus-per-task=16
# this is the file your ourput and errors go to
#SBATCH --output=./output.<specific analysis name>.txt
#SBATCH --error=./error.<specific analysis name>.txt
#SBATCH --qos=phyto

/home/summerschool/anaconda3/envs/summerschool/bin/bwa mem -t 16 <genome sequence> <1 fastq> <2 fastq> | \ 
/home/summerschool/anaconda3/envs/summerschool/bin/samtools sort -O BAM -o alingment.sorted.bam --write-index -@ 16

```

## SBATCH file for pilon

```text
#!/bin/bash
# the name of your job
#SBATCH --job-name=<job name>
#SBATCH --cpus-per-task=16
# this is the file your ourput and errors go to
#SBATCH --output=./output.<specific analysis name>.txt
#SBATCH --error=./error.<specific analysis name>.txt
#SBATCH --qos=phyto

/home/summerschool/anaconda3/envs/summerschool/bin/pilon --genome genome.fasta --output <prefix corrected data> --frags <frags.bam>
```


## SBATCH file for augustus parallel

```bash
/home/summerschool/anaconda3/envs/medaka/bin/seqkit split  -i  <genome.fa>
```

```text
#!/bin/bash
#SBATCH --job-name=augustus_array
#SBATCH --array=1-NNN           # Modifica con il numero di contigs
#SBATCH --cpus-per-task=1
#SBATCH --output=logs/augustus_%A_%a.out
#SBATCH --error=logs/augustus_%A_%a.err


# Directory con i file .fa divisi
FASTA_DIR="/path/to/split_fasta"
OUT_DIR="/path/to/output"

# File corrente da processare
FASTA_FILE=$(ls $FASTA_DIR/*.fa | sed -n ${SLURM_ARRAY_TASK_ID}p)
BASENAME=$(basename $FASTA_FILE .fa)

# Esegui AUGUSTUS
/home/summerschool/anaconda3/envs/summerschool/bin/augustus --species=fusarium $FASTA_FILE > $OUT_DIR/${BASENAME}.gff


```

