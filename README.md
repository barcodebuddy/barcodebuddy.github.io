# barcodebuddy.github.io

###Color Balance
Calculates proportion of each nucleotide per position. If at leat 10% for each base in a "best" pair listed below is present, base will be unannotated. Otherwise if at least 10% for each base in a "better" pair is present, base will be annotated in yellow. If no pair for that instrument is present with at least 10% per base, it will be annotated in red.

#####MiSeq:
Best: AG, AT, CG, CT

#####MiniSeq,NextSeq500/550,NextSeq1000,2000,NovaSeq6000 (dual-channel base is A, no-channel base is G):
Better: AC, AG, AT, CT
Best: AG, CT

#####iSeq (:
Better: AT,CT,GT,AC
Best: AC,GT

#####NovaSeqX (dual-channel base is C, no-channel base is G):
Better: AC, CT
Best: AT, CG
