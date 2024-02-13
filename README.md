# Barcode Buddy

[barcodebuddy.github.io](https://barcodebuddy.github.io)

### How to Use
Enter indices in the text boxes, each index on a new row. Leaving one of the boxes empty will run single-indexed checking. All indices in a list must be of the same length, and use only ACTGN characters. If both boxes have text in them, dual-indexed checking will be run. The number of indices in the i7 and i5 must match in this case.

&nbsp;

### Color Balance
Calculates proportion of each nucleotide per position. If at least 10% for each base in a "best" pair listed below is present, it will be unannotated for "best". Otherwise if at least 10% for each base in a "better" pair is present, it will be annotated in yellow for "okay". If at least 66% of the total bases at that position are a combination considered particularly poor, it will be annotated dark red for "very poor". Otherwise, if no "best" or "better" pair for that instrument is present with at least 10% per base, it will be annotated light red for "poor".

##### MiSeq:
Best: AG, AT, CG, CT

##### MiniSeq, NextSeq500/550, NextSeq1000/2000, NovaSeq6000 (dual-channel base is A, no-channel base is G):
Best: AG, CT, AA

Better: AC, AG, AT, CT

##### iSeq (dual-image base is A, neither-image base is G):
Best: AC, GT

Better: AT, CT, GT, AC

##### NovaSeqX/X+ (dual-channel base is C, no-channel base is G):
Best: AT, CG

Better: AC, CT, CC

Very Poor: AG, mono-A, mono-G

&nbsp;

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

### Collision Checking

For mismatch tolerance *n*, the minimum Hamming distance required between any pair of indices will be 2n + 1. This can be seen as follows:

Given sequences X and Y of arbitrary but equal length that are identical except in 2n positions, we can construct a third sequence that is <= n away from both of them with the following rules. If both sequences have the same sequence at the position, use the same base for the third string. If the sequences differ, then use the base from sequence X until we have used n bases from sequence X, then use the base from sequence Y from then on.

For example, let mismatch tolerance n = **2**, X = **AAAAAA**, Y = **ATTTTA**. X and Y are 4 apart in Hamming distance, differing at positions 2-6.

Following the above rules, we can construct A (same base) + AA (first n bases of sequence X) + TT (remaining bases from sequence Y) + A = **AAATTA**

This sequence is 2 away from both X (positions 4 and 5) and Y (positions 2 and 3), and thus would be an ambiguous barcode at mismatch tolerance 2. Mismatch tolerance must be lowered, or a more distinct pair of barcodes must be used, to avoid this.

----

For a dual-indexed run, in  BCL Convert v3.10.5 - v4.0.3 both indices must be independently distinct to be considered valid in combination. In other versions of BCL Convert and other demultiplexing workflows, the indices being distinct in combination is sufficient regardless of potential ambiguity when considered separately.
