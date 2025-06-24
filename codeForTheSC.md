# To access the remote PC

```bash
ssh <user name>@79.49.53.20
```
```bash
ssh <user name>@10.144.91.192
```

# To enter the folder where the data are

```bash
cd /home/summerschool/summerschoolFolder
```

or 

if you are in "summerschool@zeuspv:$~/"

```bash
cd summerschoolFolder
```

```bash
cd /home/summerschool/summerschoolFolder --> cd ~/summerschoolFolder
```

# To modify a file in bash, you can use

```bash
nano <file name>
```

# The first sbatch file we made lok like this

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

# SBATCH file for fastqc

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