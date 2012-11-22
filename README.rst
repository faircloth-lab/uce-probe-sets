UCE-probe-sets
==============

Files in this directory represent standardized outgroup data from 
various sets of target enrichment probes used for enriching UCE data 
from various groups organisms (e.g. see [Fair:2012a]_).

At the moment, the organisms having UCE/outgroup data are limited to 
tetrapods.  This list will soon expand to include fishes.

Probe designs, genomic positions of designed probes, fasta slices 
around genomic positions of designed probes, and outgroup UCE loci 
generated from fasta slices are avaialable for various sets of
probes.

Usage
-----

You are free to use these data in your analyses.  If you use
the ougroup data here, please reference [Fair:2012a]_ and this
website. You can provide the version of the data you used or provide 
the hash of the commit you used in the text of your manuscript, if
so desired.

All of the genomic data used to generate these files are available 
publicly.  You should reference the source of a given genomic build 
in your Literature Cited.  A good list to find all of these sources 
is available by finding a given build on the `UCSC Genome Browser`_ 
and looking at the build details.


Version control
---------------

Files in this directory are version controlled, so if you are 
looking for earlier outgroup data sets, please click the tags_ link 
above to access these earlier versions.

Minor changes to the text of these documents or additional of
explanatory details will generally result in a minor version
bump (e.g., v3.0 to v3.1).  Major changes to the contents of the
repository (due to error or addition of new probes/taxa) will
result in a major version bump (e.g., v3.0 to v4.0).


Working versions
----------------

Working versions of outgroup data may differ, as I prepare them.  
The working versions may be accessed from the `working branch`_ of 
the repository.


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

- **genome-sequence-location.conf** provides the genome versions used 
  to build the standardized UCE data sets and their location on my 
  machine (the latter bits) are not likely to be useful to anyone 
  but me
- **README.rst** is the file your're current reading
- **STEPS.rst** is a file describing the data generation steps
- **uce-2.5k-probe-set** contains probe designs for the 2.5k probe set 
  and fasta slices,lastz results, and outgroup data for these probe 
  matches against the genomes in 
  **genome-sequence-location.conf** as described below.
- **uce-5k-probe-set** contains probe designs for the 5k probe set and 
  fasta slices, lastz results, and outgroup data for these probe 
  matches against the genomes in 
  **genome-sequence-location.conf** as described below.

The standardized UCE data are useful in several circumstances.  
Within each probe-specific folder (e.g. uce-2.5k-probe-set) there
are several files:

- **uce-2.5k-probes.fasta** provides the probe sequences we designed 
  to data from 2.5k UCE loci
- **uce-2.5k-probes.fasta.toself.lastz** contains a mapping of probes 
  to themselves to ensure that probes are unique across the set
- **uce-2.5k-probes.sqlite** is a database providing summary lastz 
  data showing the mapping of probes to the various outgroup genomes 
  in **genome-sequence-location.conf**
- **outgroup-lastz** is a directory containing the lastz results used 
  to build the **uce-2.5k-probes.sqlite** database
- **outgroup-fasta** is a directory containing the read sliced from 
  the various outgroup genomes in **genome-sequence-location.conf** 
  and used to build the UCE loci in **outgroup-loci**
- **outgroup-loci** is a directory containing probe.matches.sqlite 
  database and assembled contigs representing UCE loci for the taxa 
  included.  The data within this directory is useful for 
  incorporating outgroup data to other UCE data sets as described in 
  the **phyluce documentation**_

References
----------

.. [Fair:2012a] Faircloth BC, McCormack JE, Crawford NG, Harvey MG, Brumfield RT, Glenn TC (2012). Ultraconserved Elements Anchor Thousands of Genetic Markers Spanning Multiple Evolutionary Timescales. Systematic Biology 61: 717â€“726. pmid: `22232343 <http://www.ncbi.nlm.nih.gov/pubmed?term=22232343%5Buid%5D>`_ doi: `10.1093/sysbio/SYS004 <http://dx.doi.org/10.1093/sysbio/SYS004>`_.

.. _UCSC Genome Browser: http://hgdownload.cse.ucsc.edu/downloads.html
.. _phyluce: https://github.com/faircloth-lab/phyluce
.. _phyluce documentation: http://faircloth-lab.github.com/phyluce/
.. _working branch: https://github.com/faircloth-lab/uce-probe-sets/tree/working
.. _STEPS: https://github.com/faircloth-lab/uce-probe-sets/blob/working/STEPS.rst
.. _tags: https://github.com/faircloth-lab/phyluce/tags
.. _this file: genome-sequence-location.conf
