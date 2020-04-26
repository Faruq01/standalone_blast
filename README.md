# Introduction

This tutorial aims to show familiarize with the standalone blast program. In order to perform custom blast search this tool especially useful.

# Installation 

Open the command line in linux and type the following code to install ncbi-blast in your local machine.

```sudo apt-get install ncbi-blast+```

# Create a custom datbase

Create a folder where you want to keep your custom database. Copy the fasta file you want to use a database in the folder. 

If you have a fasta file named ```nucleotide.fasta``` containing ```nucleotide sequeces``` then run the following code on the commandline. 

```makeblastdb -in nucleotide.fasta -out nucleotide.db -dbtype nucl -parse_seqids```

However, If you have a fasta file named ```protein.fasta``` containing ```protein sequeces``` then run the following code on the commandline. 

```makeblastdb -in protein.fasta -out protein.db -dbtype prot -parse_seqids```

Notice, the -dbtype is different for different file type. Also, change the name of fasta file and database as per your interest !!!

# Perform Nucleotide-nucleotide BLAST (blastn)

Here, both query and database are of nucletide sequences. Assuming, you have a query sequence file named ```file.fasta``` containing nucleotide sequences and your database containing nucleotide sequences, you can run the following command:

```blastn -query file.fasta -db nucleotide.db -out result.csv -outfmt 10```

# Perform Protein-protein BLAST (blastp)

Here, both query and database are of protein sequences. Assuming, you have a query sequence file named ```file.fasta``` containing protein sequences and your database containing protein sequences, you can run the following command:

```blastn -query file.fasta -db protein.db -out result.csv -outfmt 10```

# Nucleotide 6-frame translation-protein (blastx)

Here, the query contains nucleotide sequences and database contain protein sequences. This program compares the six-frame conceptual translation products of a nucleotide query sequence (both strands) against a protein sequence database. Assuming, you have a query sequence file named ```file.fasta``` containing nucleotide sequences and your database containing protein sequences, you can run the following command: 

```blastn -query file.fasta -db protein.db -out result.csv -outfmt 10```

### The output files are csv files with no header. Add the header as follows:
query,subject,percent_identity,alignment,mismatch,gap,q_start,q_end,s_start,s_end,evalue,bit

You can use the following code to add the header using commandline. This can be useful for large files.

```sed -i '1iquery,subject,percent_identity,alignment,mismatch,gap,q_start,q_end,s_start,s_end,evalue,bit' result.csv```

