UCE-probe-sets
==============

Files in this directory include bait designs and standardized outgroup data from 
various sets of target enrichment probes used for collecting UCE data 
from tetrapod organisms (e.g. see [Fair:2012a]_).

Probe designs, genomic positions of designed probes, fasta slices 
around genomic positions of designed probes, and outgroup UCE loci 
generated from fasta slices are avaialable for various sets of
baits.

Usage
-----

You are free to use these data in your analyses.  If you use
the bait designs or outgroup data here, please reference [Fair:2012a]_ and this
website. You can provide the version of the data you used or provide 
the hash of the commit you used in the text of your manuscript, if
so desired.

All of the genomic data used to generate these files are available 
publicly.  You should reference the source of a given genomic build 
in your Literature Cited.  A good list to find all of these sources 
is available by finding a given build on the `UCSC Genome Browser`_ 
and looking at the build details.

.. [Fair:2012a] Faircloth BC, McCormack JE, Crawford NG, Harvey MG, Brumfield RT, Glenn TC (2012). Ultraconserved Elements Anchor Thousands of Genetic Markers Spanning Multiple Evolutionary Timescales. Systematic Biology 61: 717-726. pmid: `22232343 <http://www.ncbi.nlm.nih.gov/pubmed?term=22232343%5Buid%5D>`_ doi: `10.1093/sysbio/SYS004 <http://dx.doi.org/10.1093/sysbio/SYS004>`_.

Bait Availability
-----------------

The tetrapod bait designs in this repository are available as commercially 
produced "capture-kits" from `Arbor Biosciences`_.

Organization of this Repository
-------------------------------

This repository is organized into `V1` and `V2` directories.  The `V1` directory
includes "older" bait design files that were described in [Fair:2012a]_.  There is a `README`
file within this directory describing its structure.

The `V2` directory includes "newer" bait design files where we have updated the `V1`
bait set to remove underperforming loci, standardized bait number per locus (to 2 or 4), provided
one design for enriching "high-quality" sequencing libraries (`5kV2A`) and another design for enriching
"low-quality" sequencing libraries (`5kV2B`). The `V2` bait set is largely an improvement
on `V1`, although these particular files have been especially tailored for working
with birds. 


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


.. _UCSC Genome Browser: http://hgdownload.cse.ucsc.edu/downloads.html
.. _Arbor Biosciences: https://arborbiosci.com/products/targeted-ngs/mybaits-predesigned-kits/mybaits-expert-predesigned-panels/mybaits-expert-uce/