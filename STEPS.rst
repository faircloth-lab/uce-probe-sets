Steps used to generate standardized UCE outgroup data
=====================================================

Below are the steps that I used to generate the standardized UCE locus/outgroup data.
I generated these data using phyluce_ (commit: 5d3ad3078e) on 11/21/2012.

At the top level of the repository are several files:

- **genome-sequence-location.conf** provides the genome versions 
  used to build the standardized UCE data sets and their location on
  my machine (the latter bits) are not likely to be useful to anyone 
  but me
- **README.rst** is the file your're current reading
- **STEPS.rst** is a file describing the data generation steps
- **uce-2.5k-probe-set** contains probe designs for the 2.5k probe 
  set and fasta slices,lastz results, and outgroup data for these 
  probe matches against the genomes in 
  **genome-sequence-location.conf** as described below.
- **uce-5k-probe-set** contains probe designs for the 5k probe set 
  and fasta slices, lastz results, and outgroup data for these probe 
  matches against the genomes in 
  **genome-sequence-location.conf** as described below.

The standardized UCE data are useful in several circumstances.  
Within each probe-specific folder (e.g. uce-2.5k-probe-set) there
are several files:

- **uce-2.5k-probes.fasta** provides the probe sequences we designed 
  to data from 2.5k UCE loci
- **uce-2.5k-probes.fasta.toself.lastz** contains a mapping of 
  probes to themselves to ensure that probes are unique across the set
- **uce-2.5k-probes.sqlite** is a database providing summary lastz 
  data showing the mapping of probes to the various outgroup genomes 
  in **genome-sequence-location.conf**
- **outgroup-lastz** is a directory containing the lastz results 
  used to build the **uce-2.5k-probes.sqlite** database
- **outgroup-fasta** is a directory containing the read sliced from 
  the various outgroup genomes in **genome-sequence-location.conf** 
  and used to build the UCE loci in **outgroup-loci**
- **outgroup-loci** is a directory containing probe.matches.sqlite 
  database and assembled contigs representing UCE loci for the taxa 
  included.  The data within this directory is useful for 
  incorporating outgroup data to other UCE data sets as described in 
  the `phyluce documentation`_


.. _phyluce: https://github.com/faircloth-lab/phyluce
.. _phyluce documentation: http://faircloth-lab.github.com/phyluce/


2.5k probe set
--------------

- make output dir for lastz files::

    mkdir outgroup-lastz

- copy over uce-3k-probe-set.fasta and rename to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set::

    mkdir uce-2.5k-probe-set
    cp ~/Working/UCE-overlaps/uce-3k-probes.fasta ./uce-2.5k-probe-set

- run the 2.5k probeset against genome assemblies:

    python ~/git/phyluce/bin/align/run_multiple_lastzs_sqlite.py \
        uce-2.5k-probes.sqlite \
        outgroup-lastz \
        uce-2.5k-probes.fasta \
        --scaffoldlist galGal4 melGal2 aptFor1 pygAde1 colLiv1 anoCar2 chrPic1 pelSin1 allMis1 croPor1 gavGan1 xenTro3 latCha1 pytMol1 bosTau7 loxAfr3 geoFor1 \
        --chromolist hg19 mm10 canFam3 monDom5 equCab2 taeGut1 \
        --cores 23

- slice out fastas from each respective genome, after setting up the conf file `genome-sequence-location.conf`::

    python ~/git/phyluce/bin/share/slice_sequence_from_genomes.py \
        ../genome-sequence-location.conf \
        outgroup-lastz \
        outgroup-fasta \
        --flank=2000 \
        --name-pattern "uce-2.5k-probes.fasta_v_{}.lastz.clean"

    1985 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/hg19.fasta
    1626 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/mm10.fasta
    2027 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/canFam3.fasta
    2091 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/monDom5.fasta
    1938 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/equCab2.fasta
    2541 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/taeGut1.fasta
    2591 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/galGal4.fasta
    2423 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/melGal2.fasta
    2537 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/aptFor1.fasta
    2546 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/pygAde1.fasta
    2525 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/colLiv1.fasta
    2476 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/anoCar2.fasta
    2344 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/chrPic1.fasta
    2513 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/pelSin1.fasta
    2516 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/allMis1.fasta
    2527 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/croPor1.fasta
    2531 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/gavGan1.fasta
    887 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/xenTro3.fasta
    1170 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/latCha1.fasta
    2086 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/pytMol1.fasta
    1923 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/bosTau7.fasta
    1854 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/loxAfr3.fasta
    2533 sequences written to /nfs/data1/uce-probe-sets/uce-2.5k-probe-set/outgroup-fasta/geoFor1.fasta

- align probes to themselves as a double-check::
    
    python ~/git/phyluce/bin/share/easy_lastz.py \
        --target uce-2.5k-probes.fasta \
        --query uce-2.5k-probes.fasta \
        --identity 85 \
        --output uce-2.5k-probes.fasta.toself.lastz

- make output folder::

    mkdir outgroup-loci

- assemble contigs from the genomic reads that we just sliced::

    python ~/git/phyluce/bin/share/assemble_contigs_from_genomes_universal_names.py \
        uce-2.5k-probes.fasta \
        outgroup-lastz \
        outgroup-fasta \
        outgroup-loci \
        --dupefile uce-2.5k-probes.fasta.toself.lastz \
        --db outgroup-loci/probe.matches.sqlite \
        --pattern "uce-2.5k-probes.fasta_v_(.*).lastz.clean"

- commit to repo (currently in working version)

5k probe set
------------

- make output dir for lastz files::

    mkdir outgroup-lastz

- run the 5k probeset against genome assemblies:

    python ~/git/phyluce/bin/align/run_multiple_lastzs_sqlite.py \
        uce-5k-probes.sqlite \
        outgroup-lastz \
        uce-5k-probes.fasta \
        --scaffoldlist galGal4 melGal2 aptFor1 pygAde1 colLiv1 anoCar2 chrPic1 pelSin1 allMis1 croPor1 gavGan1 xenTro3 latCha1 pytMol1 bosTau7 loxAfr3 geoFor1 \
        --chromolist hg19 mm10 canFam3 monDom5 equCab2 taeGut1 \
        --cores 23

- make ouput dir::

    mkdir outgroup-fasta

- slice out fastas from each respective genome, after setting up the conf file `genome-sequence-location.conf`::

    python ~/git/phyluce/bin/share/slice_sequence_from_genomes.py \
        ../genome-sequence-location.conf \
        outgroup-lastz \
        outgroup-fasta \
        --flank=2000 \
        --name-pattern "uce-5k-probes.fasta_v_{}.lastz.clean"

    3888 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/hg19.fasta
    3128 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/mm10.fasta
    3936 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/canFam3.fasta
    4129 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/monDom5.fasta
    3734 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/equCab2.fasta
    5358 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/taeGut1.fasta
    5507 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/galGal4.fasta
    5176 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/melGal2.fasta
    5407 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/aptFor1.fasta
    5415 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/pygAde1.fasta
    5332 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/colLiv1.fasta
    4932 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/anoCar2.fasta
    4905 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/chrPic1.fasta
    5182 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/pelSin1.fasta
    5307 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/allMis1.fasta
    5294 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/croPor1.fasta
    5310 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/gavGan1.fasta
    1652 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/xenTro3.fasta
    2108 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/latCha1.fasta
    3969 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/pytMol1.fasta
    3750 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/bosTau7.fasta
    3608 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/loxAfr3.fasta
    5274 sequences written to /nfs/data1/uce-probe-sets/uce-5k-probe-set/fasta-2000-flank/geoFor1.fasta

- align probes to themselves as a double-check::
    
    python ~/git/phyluce/bin/share/easy_lastz.py \
        --target uce-5k-probes.fasta \
        --query uce-5k-probes.fasta \
        --identity 85 \
        --output uce-5k-probes.fasta.toself.lastz

- make output folder::

    mkdir outgroup-loci

- assemble contigs from the genomic reads that we just sliced::

    python ~/git/phyluce/bin/share/assemble_contigs_from_genomes_universal_names.py \
        uce-5k-probes.fasta \
        outgroup-lastz \
        outgroup-fasta \
        outgroup-loci \
        --dupefile uce-5k-probes.fasta.toself.lastz \
        --db outgroup-loci/probe.matches.sqlite \
        --pattern "uce-5k-probes.fasta_v_(.*).lastz.clean"

- commit to repo (currently in working version)
