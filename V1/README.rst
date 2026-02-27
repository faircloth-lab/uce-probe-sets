Genomic data and data generation STEPS
--------------------------------------

The specific genome builds used for slicing data and generating outgroup UCE loci are detailed within `this file`_.

The STEPS used to align probes, slice fastas, and assemble contigs are available within the STEPS_ file.

At present, the UCE outgroup loci in `outgroup-loci` represent the
UCE locus ± 500 bp, for a total locus length of ~ 1120 bp, on
average.


Contents
--------

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

.. _UCSC Genome Browser: http://hgdownload.cse.ucsc.edu/downloads.html
.. _phyluce: https://github.com/faircloth-lab/phyluce
.. _phyluce documentation: http://faircloth-lab.github.com/phyluce/
.. _STEPS: STEPS.rst
.. _tags: https://github.com/faircloth-lab/phyluce/tags
.. _this file: genome-sequence-location.conf
