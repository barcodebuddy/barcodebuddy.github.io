# barcodebuddy.github.io

### Color Balance
Calculates proportion of each nucleotide per position. If at least 10% for each base in a "best" pair listed below is present, base will be unannotated. Otherwise if at least 10% for each base in a "better" pair is present, base will be annotated in yellow. If no pair for that instrument is present with at least 10% per base, it will be annotated in red. If at least 66% of the total bases at that position are a combination considered particularly poor, it will be annotated dark red.

**Ex, NovaSeqX i7 index sequences as follows:**

* ACTC

* GAGA

* AGTC

* ATTA

Position 1 is 75% A, 25% G. Because there is neither 10% C nor 10% T present, none of the "better" or "best" pairs are present. 100% of the bases are A or G, so the position is annotated as "very poor".

Position 2 has 25% of each base, and thus at least 10% of both A and T (as well as C and G). The position is annotated as "best".

Position 3 has 75% T and 25% G. With no A or C present this does not meet any of the requirements of the "better" or "best" pairs. However, it does have enough A + G to meet the requirements of "very poor", so it is annotated as "poor".

Position 4 has 50% A and 50% C. This is not one of the "best" pairs, but it is one of the "better" pairs, so the position is annotated as "better".

&nbsp;

##### MiSeq:
Best: AG, AT, CG, CT

##### MiniSeq,NextSeq500/550,NextSeq1000,2000,NovaSeq6000 (dual-channel base is A, no-channel base is G):
Better: AC, AG, AT, CT
Best: AG, CT

##### iSeq (dual-image base is A, neither-image base is G):
Best: AC,GT
Better: AT,CT,GT,AC

##### NovaSeqX (dual-channel base is C, no-channel base is G):
Best: AT, CG
Better: AC, CT
Very Poor: AG, mono-A, mono-G
