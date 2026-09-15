# Results Summary — RB1 Mutation Analysis

## Part V — Wild-Type Control
| Metric | Value |
|---|---|
| CDS length (nt) | 2787 |
| Predicted protein length (aa) | 928 |
| Start codon | ATG |
| Stop codon | TGA |
| Reading frame | Frame 1 |
| First 10 aa | MPPKTPRKTA |

## Part VIII — Documented Mutation (c.373G>T, p.Glu125Ter)
| Metric | Value |
|---|---|
| Mutant CDS length | 2787 nt (unchanged) |
| Real biological protein length | 124 aa |
| Reading frame | Unchanged |
| First difference from WT | Position 125 |
| Premature stop codon | Yes, at codon 125 |
| Amino acids lost | 804 (of 928) |

**Note:** transeq translates through internal stop codons rather than
terminating there. The raw output was manually truncated at the first
`*` to reflect the biologically accurate protein product before
alignment.

## Part IX — WT vs. Documented Mutant Alignment (corrected)
| Metric | Value |
|---|---|
| Region of identity | Positions 1–124 (100% identical to WT) |
| Divergence point | Position 125 onward |
| Mutant protein length | 124 aa |
| WT protein length | 928 aa |
| Amino acids lost | 804 (89% of protein) |

## Part XI — Artificial Mutation (1-nt deletion, position 151)
| Metric | Value |
|---|---|
| Mutant CDS length | 2786 nt (not divisible by 3) |
| Real biological protein length | 63 aa |
| Reading frame | Shifted starting at codon 51 |
| First difference from WT | Position 51 |
| Premature stop codon | Yes, at position 64 |
| Sequence composition | aa 1–50 identical to WT; aa 51–63 scrambled/nonsense; then stop |

## Part XII — Comparison Table
| Feature | WT | Documented (Nonsense) | Artificial (Frameshift) |
|---|---|---|---|
| CDS length | 2787 nt | 2787 nt | 2786 nt |
| Divisible by 3? | Yes | Yes | No |
| Protein length | 928 aa | 124 aa | 63 aa |
| Mutation type | — | Nonsense | Frameshift |
| Reading frame changed? | — | No | Yes |
| Premature stop? | — | Yes (codon 125) | Yes (codon 64) |
| First difference | — | Position 125 | Position 51 |
| Nature of loss | — | Clean truncation; everything before stop is correct | Scrambled sequence from position 51 onward, then random stop |
