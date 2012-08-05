We built these files using [phyluce commmit 7ea81cc80c](https://github.com/faircloth-lab/phyluce/commit/7ea81cc80ca05926ca44a9928321f6de52d8f98e)

* align probes to other reference genomes:

    ```python
    python ~/git/phyluce/bin/share/run_many_lastzs.py \
        outgroup.conf \
        faircloth-2500-probes.fasta \
        outgroup-lastz \
        --nprocs 12
    ```

* slice reads from genome sequences given results in outgroup-lastz:

    ```python
    python ~/git/phyluce/bin/share/slice_sequence_from_genomes.py \
        outgroup.conf \
        outgroup-lastz \
        outgroup-fasta \
        --flank=500

    2572 sequences written to /nfs/data1/probes/2500-probes/outgroup-fasta/gallus_gallus.fasta
    1985 sequences written to /nfs/data1/probes/2500-probes/outgroup-fasta/homo_sapiens.fasta
    1630 sequences written to /nfs/data1/probes/2500-probes/outgroup-fasta/mus_musculus.fasta
    2541 sequences written to /nfs/data1/probes/2500-probes/outgroup-fasta/zebra_finch.fasta
    2091 sequences written to /nfs/data1/probes/2500-probes/outgroup-fasta/monodelphis_domestica.fasta
    2476 sequences written to /nfs/data1/probes/2500-probes/outgroup-fasta/anolis_carolinensis.fasta
    2517 sequences written to /nfs/data1/probes/2500-probes/outgroup-fasta/crocodylus_porosus.fasta
    2423 sequences written to /nfs/data1/probes/2500-probes/outgroup-fasta/meleagris_gallopavo.fasta
    2516 sequences written to /nfs/data1/probes/2500-probes/outgroup-fasta/alligator_mississippiensis.fasta
    ```

* generate probe-probe alignments for dupe check:

    ```python
    python ~/git/phyluce/bin/share/easy_lastz.py \
        --target faircloth-2500-probes.fasta \
        --query faircloth-2500-probes.fasta \
        --identity 85 \
        --output faircloth-2500-probes.fasta.toself.lastz
    ```

* take reads sliced for individual probes and (where necessary) assemble
  those to contigs:

    ```python
    python ~/git/phyluce/bin/share/assemble_contigs_from_genomes.py \
        faircloth-2500-probes.fasta \
        outgroup-lastz \
        outgroup-fasta \
        outgroup-loci \
        --dupefile faircloth-2500-probes.fasta.toself.lastz \
        --oldprobe

    Database already exists.  Overwrite [Y/n]? Y
    Determining duplicate probes...

    ==============================
    gallus_gallus
    ==============================
        Getting LASTZ matches from GENOME alignments...
        Getting bad (potentially duplicate) GENOME matches...
        Skipping 12 bad (duplicate hit) loci...
        Output filename is gallus-gallus.fasta
        Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci)...
        2374 loci of 2386 matched (99%), 12 dupes dropped (1%), 2374 (99%) kept

    ==============================
    crocodylus_porosus
    ==============================
        Getting LASTZ matches from GENOME alignments...
        Getting bad (potentially duplicate) GENOME matches...
        Skipping 3 bad (duplicate hit) loci...
        Output filename is crocodylus-porosus.fasta
        Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci)...
        2337 loci of 2386 matched (98%), 3 dupes dropped (0%), 2337 (98%) kept

    ==============================
    monodelphis_domestica
    ==============================
        Getting LASTZ matches from GENOME alignments...
        Getting bad (potentially duplicate) GENOME matches...
        Skipping 23 bad (duplicate hit) loci...
        Output filename is monodelphis-domestica.fasta
        Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci)..
        1874 loci of 2386 matched (79%), 23 dupes dropped (1%), 1874 (79%) kept

    ==============================
    mus_musculus
    ==============================
        Getting LASTZ matches from GENOME alignments...
        Getting bad (potentially duplicate) GENOME matches...
        Skipping 16 bad (duplicate hit) loci...
        Output filename is mus-musculus.fasta
        Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci)..
        1440 loci of 2386 matched (60%), 16 dupes dropped (1%), 1440 (60%) kept

    ==============================
    homo_sapiens
    ==============================
        Getting LASTZ matches from GENOME alignments...
        Getting bad (potentially duplicate) GENOME matches...
        Skipping 21 bad (duplicate hit) loci...
        Output filename is homo-sapiens.fasta
        Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci)..
        1765 loci of 2386 matched (74%), 21 dupes dropped (1%), 1765 (74%) kept

    ==============================
    alligator_mississippiensis
    ==============================
        Getting LASTZ matches from GENOME alignments...
        Getting bad (potentially duplicate) GENOME matches...
        Skipping 4 bad (duplicate hit) loci...
        Output filename is alligator-mississippiensis.fasta
        Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci)...
        2334 loci of 2386 matched (98%), 4 dupes dropped (0%), 2334 (98%) kept

    ==============================
    anolis_carolinensis
    ==============================
        Getting LASTZ matches from GENOME alignments...
        Getting bad (potentially duplicate) GENOME matches...
        Skipping 27 bad (duplicate hit) loci...
        Output filename is anolis-carolinensis.fasta
        Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci)...
        2249 loci of 2386 matched (94%), 27 dupes dropped (1%), 2249 (94%) kept

    ==============================
    meleagris_gallopavo
    ==============================
        Getting LASTZ matches from GENOME alignments...
        Getting bad (potentially duplicate) GENOME matches...
        Skipping 6 bad (duplicate hit) loci...
        Output filename is meleagris-gallopavo.fasta
        Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci)...
        2241 loci of 2386 matched (94%), 6 dupes dropped (0%), 2241 (94%) kept

    ==============================
    zebra_finch
    ==============================
        Getting LASTZ matches from GENOME alignments...
        Getting bad (potentially duplicate) GENOME matches...
        Skipping 2 bad (duplicate hit) loci...
        Output filename is zebra-finch.fasta
        Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci)...
        2363 loci of 2386 matched (99%), 2 dupes dropped (0%), 2363 (99%) kept
    ```

