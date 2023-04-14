# Colby Griffin
Lab Notebook

Ps1='$ ' 
# get rid of variable on command line 

cd
# change directory, name the folder after command to get it pulled up

rm 
# remove, will delete files in dolfer

ssh username@servername.edu
# connects my terminal to the teaching cluster ron computer

ls
# All of the files in my current working directory

pwd
# this stamds for print working directory

Control c
# clears the current command line and makes a new one

Lab 2 Starts 02/10/23

mkdir name of directory
# Make directory

cp
# Copy a file

tar -zxf 
# Tells tar file to decompress, zxf are all different options for doing this, new directory should appear after hitting ls, thats not .tar

ls -F. -lrth
# options for ls to dislay more information about directories

head (file name)
# open fastq files or all files

man (command)
# pulls up manual for command 

command --help 
# gives help on what each command does

grep '@SRR097977' SRR097977.fastq | wc
# searches through files for information you enter after it, like above. | wc is word count, -l gives number of lines
'info you want' files name

Pressing up or down arrows 
# naviagtes thorugh previous commands ypuve evtered and puts them in the command line

cd ~
# brings you back to your base directory

Lab 3 Starts 2/17/2023

../
# Goes one directory backwards

hit tab twice
# shows options to go forward with command you already have in command line

cd /
# starts an absolute path

cd /home/users/cmg1126/gen711
# will get you back to gen711 from where you are

Excersize 3a three ways to get back to home directory
1. cd ~
2. cd /home.users/cmg1126
3. cd ../../../

ls -a
# reveals hidden directories

cat
# opens files or sticking files together, usefull for sticking samples together to make larger sequences

*.fastq   c*
# lists all files with what follows the wildcard, place it where you need it. if looking for files thatastart witha letter, put * first

excersize list all aplications on ron that start with c
c- 90
a- 45
o- 22

ls /
# shows all programs on supercomputer

echo
# takes what you put on command line and copies it to next line

> redirect
# send command before it into a file

>> append
# adds new data to file instad of overwriting it

control r
# searchs your history for commands

history | grep 'what youre looking for'
# find all commands ever used with words in quotes

-A2 -B1
# keep two lines below and one line above requested grep

Lab 4 2/24/2023 Starts

realpath foldername
# shows the absolute path for a folder 

curl -O website address
# pull data from a website online and downloads it

gunzip filename
# unzips g zip flders 

bg 
# puts process in bakground to get command line back

Control Z
# pauses command going, stops dowlaod or unzpiping

top
# gives lsit of all programs running on supercomputer

less -S
# open file like cat but lets yous scroll though it

tail
# pulls up last read in a file

ls -s -h    can use -l instead of -s
# shows file size in human readable form 

conda activate genomics
# moves you from base envirnoment with no programs to genomics environemnt 

fastqc 
# shows qauity of sequences for you

mv filename ~/directory youre putting it in
# moves files 

uunzip
# unzips zips files

Lab 05 starts 3/3/2023

sftp
# secure file operation in terminal

get filename in sftp
# retrives file or pciture and opens it 

trimmomatic PE -threads 4 SRR_1056_1.fastq SRR_1056_2.fastq \
SRR_1056_1.trimmed.fastq.gz SRR_1056_1un.trimmed.fastq.gz \
SRR_1056_2.trimmed.fastq.gz SRR_1056_2un.trimmed.fastq.gz \
ILLUMINACLIP:SRR_adapters.fa SLIDINGWINDOW:4:20
# used for trimming fastq

-threads number
# tells how many cpu's power to use in command 

for infile in *_1.fastq.gz
do
    base=$(basename ${infile} _1.fastq.gz)
    trimmomatic PE ${infile} ${base}_2.fastq.gz \
    ${base}_1.trim.fastq.gz ${base}_1un.trim.fastq.gz \
    ${base}_2.trim.fastq.gz ${base}_2un.trim.fastq.gz \
    SLIDINGWINDOW:4:20 MINLEN:25 ILLUMINACLIP:NexteraPE-PE.fa:2:40:15
done
# sets a loop to have program run over and over (for)

1. make a folder called ‘trimmed_fastq’ in data
# mkdir trimmed fastq
2. move all files that we made (hint: .trim and the move command, and the destination directory will work)
# cp /tmp/trimmed/*.gz ~/dc_workshop/data/trimmed_fastq/ 
3. Re-run fastqc on the trimmed fastqs in the trimmed_fastq folder.
# fastqc *fastq.gz

Lab 6 starts 3/24/23

curl -L -o /data/ref_genome (url)
# pulls data from online 

mv 
# moves folder

bwa mem (bwa mem data/ref_genome/ecoli_rel606.fasta data/trimmed_fastq_small/SRR2584866_1.trim.sub.fastq)
# in genomics plus runs genome alignment

grep -v  'what you dont want' 
# inverse grep, pull everything without what you tell it to  pull

samtool -sort
# used for changing sam files to bam files

Lab 7 starts 3/31/2023

SRR2589044.aligned.sorted.bam
# my aligned file from last week

Files for ref genome
/home/users/cmg1126/dc_workshop/data/ref_genome/ecoli_rel606.fasta
/home/users/cmg1126/dc_workshop/data/ref_genome/ecoli_rel606.fasta.amb
/home/users/cmg1126/dc_workshop/data/ref_genome/ecoli_rel606.fasta.ann
/home/users/cmg1126/dc_workshop/data/ref_genome/ecoli_rel606.fasta.bwt
/home/users/cmg1126/dc_workshop/data/ref_genome/ecoli_rel606.fasta.fai
/home/users/cmg1126/dc_workshop/data/ref_genome/ecoli_rel606.fasta.pac
/home/users/cmg1126/dc_workshop/data/ref_genome/ecoli_rel606.fasta.sa

Files for aligned seq
/home/users/cmg1126/dc_workshop/results/bam/SRR2584866.aligned.sorted.bam
/home/users/cmg1126/dc_workshop/results/bam/SRR2584866.aligned.sorted.bam.bai

VCF files paths
/home/users/cmg1126/dc_workshop/results/vcf/SRR2584866_final_variants.vcf
/home/users/cmg1126/dc_workshop/results/vcf/SRR2584866_variants.vcf

Practice Practical 

cd /
# starts absolute path

cd 
# changes directroy

grep 'NNNNNNN' SRR098026.fastq
# greps for bad reads once in shell data folder, 7 N is seven miscalls in a row, need filename after what youre grepping for

grep -B1
# gives one line above above the lie with grep material (NNNNNNN)
grep -A2
# gives two lines below grep matieral line (NNNNNN)
grep -B1 -A2
# retunrs full four lines of fastq

grep -B1 -A2 'NNNNNNN' SRR08....fastq > badreads.txt
# redirects SRR file inot badread file. grep only takes the lines with seven N's (Bad reads) and moves all lines of data with -B1 and -A2

wc -l SRR.... (996 lines) bareads.txt (249 lines)
# givs the word count -l will make it give you line count

cp filename.fastq ../newfilename.fastq
# ../ moves file one directory back, mv will move but not copy so use cp

cat *.fastq | grep 'NNNNNNN' > badreads.txt
# adds two files together, this case will combine two fastq's, piped to a rediect command into badreads.txt

echo Colby Griffin > mynamefile
# to add name to top of file, create new one first
cat mynamefile SRR.fastq > newfile.fastq
# this will combine the two files and create anew one with my name at the top

echo Colby Griffin >> SRR.fastq
# will put your name at the end by appending

Lab notebook starts 4/14/2023

https://github.com/jthmiller/gen711-811-example













