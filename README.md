# RES_analysis
This repository contains code for calculating residue-level sequence scores using a Position Weight Matrix (PWM) and performing phylogenetic analysis using PGLS fitting. It includes two main modules: Sequence Scoring and Phylogenetic Tree Construction. The first module processes aligned sequences from a FASTA file calculates position-specific scores, and saves them to a CSV file. The second module constructs a phylogenetic tree from the aligned sequences and runs a Phylogenetic Generalized Least Squares to fit the average lifespan against RES.

## Requirements
Python:
- argparse 
- math 
- pandas 
- Biopython 
- re 

R:
- ape
- seqinr
- Biostrings
- phytools
- phangorn
- nlme

## Functionality
1. res.py module
This module is designed to calculate the log odds of sequence scores based on a Position Weight Matrix (PWM) derived from a set of aligned protein sequences and background residue frequencies for the sequences.

2. pgls_analysis
This module models species' average lifespans based on residue-level RES. It first creates a phylogenetic tree using the make_tree() method and then incorporates that tree into the model fitting of the run_pgls_analysis() method.

## Input and Output Files
Input Files:

- FASTA file: Aligned protein sequences
- CSV file: Residue-level data for PGLS analysis.

Output Files:

- CSV file: Residue-wise position scores.
- Phylogenetic tree file: Newick-format phylogenetic tree.
- PGLS results: data frame output containing the coefficients, p-values, and t-statistics from the PGLS analysis.

## Example Run
Sequence Scoring in Python:
- `python sequence_scoring.py input_sequences.fasta output_scores.csv`
- Then edit the csv file to include a column for average lifespans

Phylogenetic Tree Construction in R:
- `make_tree("aligned_sequences.fasta", "output_tree.phy")`

PGLS Analysis in R:
- `order_pgls_model <- run_pgls_analysis("output_scores.csv", "output_tree.phy", "outgroup_species")`
- `order_final_data <- order_pgls_model$results`

The order_final_data can then be subsetted to find significantly correlated residues. 

## Acknowledgments
- Biopython
- R packages
