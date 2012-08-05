Files in this directory represent the ~2500 locus probe set presented in
McCormack et al. 2012 matches to useful outgroup taxa.  These data
can be integrated with UCE capture data using the 
[phyluce](https://github.com/faircloth-lab/phyluce) pipeline.

# Genomic data are from the following releases:

* gallus_gallus [galGal3](http://hgdownload.cse.ucsc.edu/goldenPath/galGal3/bigZips/)
* homo_sapiens [hg19](http://hgdownload.cse.ucsc.edu/goldenPath/hg19/bigZips/)
* mus_musculus [mm9](http://hgdownload.cse.ucsc.edu/goldenPath/mm9/bigZips/)
* zebra_finch [taeGut1](http://hgdownload.cse.ucsc.edu/goldenPath/taeGut1/bigZips/)
* monodelphis_domestica [monDom5](http://hgdownload.cse.ucsc.edu/goldenPath/monDom5/bigZips/)
* anolis_carolinensis [anoCar2](http://hgdownload.cse.ucsc.edu/goldenPath/anoCar2/bigZips/)
* crocodylus_porosus [croPor0.1](http://crocgenomes.org/)
  ftp://ftp.crocgenomes.org/pub/crocodile.old/cpor_v0.0.1/cPorosus_v0.0.1.fa
* meleagris_gallopavo [melGal2](http://www.ncbi.nlm.nih.gov/genbank)
  ftp://ftp.ncbi.nih.gov/genbank/genomes/Eukaryotes/vertebrates_other/Meleagris_gallopavo/Turkey_2.01/Primary_Assembly/assembled_chromosomes/FASTA/)
* alligator_mississippiensis [allMis1](http://crocgenomes.org/)
  ftp://ftp.crocgenomes.org/pub/alligator.current/aMiss_AKHW01000000_sub1.fa.gz

# Steps

Steps to generate these outgroup data are in [STEPS.md](2500-probes/STEPS.md).

# Fasta data (in outgroup-fasta)

Fasta data represent genome slices from the above taxa where we located individual
probes +/- 500 bp.  Lastz matches of probes to genomes are in [outgroup-lastz](2500-probes/outgroup-lastz).

# Locus data (in outgroup-loci)

To assemble fasta slices to UCE loci, we ran the 
`phyluce/bin/share/assemble_contigs_from_genomes.py` code.  Assembled loci (these
are what you use with the `--extend` argument to `get_match_counts.py`) are in 
[outgroup-loci](2500-probes/outgroup-loci).
