We built these files using [phyluce commmit 7ea81cc80c](https://github.com/faircloth-lab/phyluce/commit/7ea81cc80ca05926ca44a9928321f6de52d8f98e)

* align probes to other reference genomes:

    ```python
    python ~/git/phyluce/bin/share/run_many_lastzs.py \
        outgroup.conf \
        faircloth-5000-probes.fasta \
        outgroup-lastz \
        --nprocs 7
    ```

* slice reads from genome sequences given results in outgroup-lastz:

    ```python
    python ~/git/phyluce/bin/share/slice_sequence_from_genomes.py \
        outgroup.conf \
        outgroup-lastz \
        outgroup-fasta \
        --flank=500
    ```

* generate probe-probe alignments for dupe check:

    ```python
    python ~/git/phyluce/bin/share/easy_lastz.py \
        --target faircloth-5000-probes.fasta \
        --query faircloth-5000-probes.fasta \
        --identity 85 \
        --output faircloth-5000-probes.fasta.toself.lastz
    ```

* take reads sliced for individual probes and (where necessary) assemble
  those to contigs:

    ```python
    python ~/git/phyluce/bin/share/assemble_contigs_from_genomes.py \
        faircloth-5000-probes.fasta \
        outgroup-lastz \
        outgroup-fasta \
        outgroup-loci \
        --dupefile faircloth-5000-probes.fasta.toself.lastz \
        --oldprobe

    Database already exists.  Overwrite [Y/n]? Y
    Determining duplicate probes...

    Database already exists.  Overwrite [Y/n]? Y
    Determining duplicate probes...

    ==============================
    alligator_mississippiensis
    ==============================
            Getting LASTZ matches from GENOME alignments...
            Getting bad (potentially duplicate) GENOME matches...
            Skipping 26 bad (duplicate hit) loci...
            Output filename is alligator-mississippiensis.fasta
            Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci).....
            4837 loci of 5064 matched (96%), 26 dupes dropped (1%), 4837 (96%) kept

    ==============================
    anolis_carolinensis
    ==============================
            Getting LASTZ matches from GENOME alignments...
            Getting bad (potentially duplicate) GENOME matches...
            Skipping 50 bad (duplicate hit) loci...
            Output filename is anolis-carolinensis.fasta
            Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci).....
            4431 loci of 5064 matched (88%), 50 dupes dropped (1%), 4431 (88%) kept

    ==============================
    crocodylus_porosus
    ==============================
            Getting LASTZ matches from GENOME alignments...
            Getting bad (potentially duplicate) GENOME matches...
            Skipping 5 bad (duplicate hit) loci...
            Output filename is crocodylus-porosus.fasta
            Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci).....
            4846 loci of 5064 matched (96%), 5 dupes dropped (0%), 4846 (96%) kept

    ==============================
    gallus_gallus
    ==============================
            Getting LASTZ matches from GENOME alignments...
            Getting bad (potentially duplicate) GENOME matches...
            Skipping 44 bad (duplicate hit) loci...
            Output filename is gallus-gallus.fasta
            Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci)......
            5020 loci of 5064 matched (99%), 44 dupes dropped (1%), 5020 (99%) kept

    ==============================
    homo_sapiens
    ==============================
            Getting LASTZ matches from GENOME alignments...
            Getting bad (potentially duplicate) GENOME matches...
            Skipping 47 bad (duplicate hit) loci...
            Output filename is homo-sapiens.fasta
            Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci)....
            3335 loci of 5064 matched (66%), 47 dupes dropped (1%), 3335 (66%) kept

    ==============================
    meleagris_gallopavo
    ==============================
            Getting LASTZ matches from GENOME alignments...
            Getting bad (potentially duplicate) GENOME matches...
            Skipping 13 bad (duplicate hit) loci...
            Output filename is meleagris-gallopavo.fasta
            Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci).....
            4756 loci of 5064 matched (94%), 13 dupes dropped (0%), 4756 (94%) kept

    ==============================
    monodelphis_domestica
    ==============================
            Getting LASTZ matches from GENOME alignments...
            Getting bad (potentially duplicate) GENOME matches...
            Skipping 58 bad (duplicate hit) loci...
            Output filename is monodelphis-domestica.fasta
            Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci)....
            3589 loci of 5064 matched (71%), 58 dupes dropped (1%), 3589 (71%) kept

    ==============================
    mus_musculus
    ==============================
            Getting LASTZ matches from GENOME alignments...
            Getting bad (potentially duplicate) GENOME matches...
            Skipping 42 bad (duplicate hit) loci...
            Output filename is mus-musculus.fasta
            Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci)...
            2624 loci of 5064 matched (52%), 42 dupes dropped (1%), 2624 (52%) kept

    ==============================
    zebra_finch
    ==============================
            Getting LASTZ matches from GENOME alignments...
            Getting bad (potentially duplicate) GENOME matches...
            Skipping 7 bad (duplicate hit) loci...
            Output filename is zebra-finch.fasta
            Writing and Aligning/Assembling UCE loci with multiple probes (dot/1000 loci).....
            4937 loci of 5064 matched (97%), 7 dupes dropped (0%), 4937 (97%) kept
    ```
