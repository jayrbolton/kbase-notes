# An overview of KBase for people without biology backgrounds

## Genes and Genomes

A *gene* is a single unit of DNA that is inheritable, while the *genome* is the entire set of genes for an organism. A gene typically contains code to produce a single type of protein.

A gene is a small segment of the DNA molecule, while the genome comprises the entire set of DNA inside of a cell.

## Genome sequencing

*Sequencing* is the process of taking cell samples and extracting DNA data. *NGS* (next generation sequencing) is a modern set of tools for gathering DNA sequences. DNA is read in fragments called *reads* that vary in quality, accuracy, and are produced out of order. One purpose of KBase is to take this fragmented data and produce a correct, ordered DNA sequence.

#### Paired-end and single-read sequencing

In Illumina sequencing, TODO

## Genome assembly

Typically you are given a large set of DNA fragments that are out of order. DNA sequencing devices aren't able to read out DNA in a continuous format, but rather in un-ordered fragments. Assembly is the process of trying to put all those fragments into the correct ordering. *Reads* is the name used for short fragments of DNA that come from sequencing.

> The problem of sequence assembly can be compared to taking many copies of a book, passing each of them through a shredder with a different cutter, and piecing the text of the book back together just by looking at the shredded pieces.

### FASTA / FASTQ formats

These are file formats that represent nucleotide or peptide sequences in a genome. You can find a full description on [the wikipedia page for FASTA](https://en.wikipedia.org/wiki/FASTA_format).

The FASTQ format contains additonal data about the *quality* of each read/fragment of DNA: [Wikipedia page](https://en.wikipedia.org/wiki/FASTQ_format).

### Trimming

Reads sometimes have junk and inaccurate data. *Trimming* is a process that removes that useless data from the reads.
