# From Gene Mutation to Disease: RB1 and Retinoblastoma

**Author:** [your name]
**Date:** [today's date]

---

## 1. Disease Background

Retinoblastoma is a malignant tumor of the developing retina that arises from biallelic inactivation of the RB1 gene in an embryonic retinal cell. It is the most common intraocular cancer in children, typically presenting before the age of five, and in some cases at birth or in infancy. The most recognizable clinical sign is leukocoria, a white or abnormal reflection seen in the pupil instead of the normal red-eye reflex, along with strabismus in some cases. The disease can be unilateral or bilateral, with bilateral cases generally reflecting the heritable form.

At the genetic level, retinoblastoma follows Knudson's two-hit hypothesis: a cell must lose function of both copies of RB1 before a tumor can form. In the heritable form, a person is born with one mutated RB1 allele in every cell, so only one additional somatic hit is needed to trigger tumor formation, which is why heritable retinoblastoma tends to be bilateral, appear earlier, and carries risk for second cancers later in life such as osteosarcoma. In the non-heritable, sporadic form, both hits must occur somatically within the same retinal cell, so sporadic cases are almost always unilateral. Although the loss-of-function mechanism is recessive at the cellular level, the germline predisposition is inherited in an autosomal dominant pattern, since carrying one mutated allele is enough to make tumor formation highly likely.

## 2. Gene and Normal Protein Function

RB1 (RB transcriptional corepressor 1) is located on chromosome 13 at 13q14.2. It spans roughly 180–200 kb of genomic DNA, organized into 27–29 exons (depending on annotation), and is transcribed into a 4.7 kb mRNA (NM_000321.3) that is translated into pRB, a 928-amino-acid nuclear phosphoprotein (NP_000312.2), approximately 106 kDa.

pRB is a tumor suppressor that negatively regulates the G1-to-S cell cycle transition. In its active, hypophosphorylated state, pRB binds E2F transcription factors through its central pocket domain (roughly residues 379–792) and represses the genes E2F would otherwise activate, holding the cell in G1. As the cell prepares to divide, cyclin D–CDK4/6 complexes phosphorylate pRB, releasing E2F and allowing progression into S phase. Because this repression occurs in the nucleus, pRB depends on a nuclear localization signal near its C-terminus (roughly residues 860–876) to be transported there. RB1 was the first tumor suppressor gene ever cloned and is a foundational model for understanding loss of cell-cycle control in cancer.

## 3. Documented Mutation

| Field | Detail |
|---|---|
| Gene / transcript | RB1, NM_000321.3 |
| Variant (nucleotide) | c.373G>T |
| Variant (protein) | p.Glu125Ter (E125*) |
| Mutation type | Nonsense |
| ClinVar accession | VCV001334098.5 (Variation ID: 1334098) |
| Classification | Pathogenic/Likely pathogenic (4 submissions) |
| Associated conditions | Retinoblastoma; Hereditary cancer-predisposing syndrome |
| dbSNP | rs1952457111 |

This variant was selected from ClinVar, where it has a two-star review status with four independent submissions consistently classifying it as pathogenic for retinoblastoma. As a nonsense mutation occurring early in the coding sequence, it was predicted to truncate the RB protein well before both the pocket domain and the C-terminal nuclear localization signal, making it a strong candidate for demonstrating loss-of-function via premature translation termination.

## 4. Hypothesis

Codon 125 falls at nucleotides 373–375 of the CDS, matching the c.373G>T notation. The wild-type codon (GAA, glutamate) becomes TAA (stop) with the G→T change. Since this is a substitution, the reading frame was predicted to remain unaffected, with only codon 125 converted from an amino acid codon to a stop signal. Translation was predicted to terminate there, producing a protein approximately 124 amino acids long, lacking essentially all functional domains downstream of residue 125, including the pocket domain and nuclear localization signal, and resulting in complete loss of function.

## 5. Methods

The RB1 reference CDS (NM_000321.3, nucleotides 163–2949) and reference protein (NP_000312.2) were retrieved from NCBI RefSeq and uploaded into Galaxy. The wild-type CDS was translated using EMBOSS transeq (Frame 1, Standard genetic code) to establish the WT protein control, which was confirmed to match the reference translation (928 aa, starting with MPPKTPRKTA...).

A copy of the WT CDS was manually edited to introduce the documented c.373G>T substitution at nucleotide 373 (GAA→TAA), without altering the original WT file. This mutant CDS was translated using the same transeq settings. Because transeq translates through internal stop codons rather than terminating there, the raw output was manually truncated at the first stop codon to reflect the biologically accurate protein product before further analysis.

Pairwise alignment between WT and mutant proteins was performed using EMBOSS needle (gap open 10.0, gap extend 0.5, EBLOSUM62 matrix).

A second, self-designed mutation was created by deleting a single nucleotide (position 151) from a fresh copy of the WT CDS, translated and analyzed using the same procedure, to compare a frameshift mutation against the documented nonsense mutation.

## 6. Results

**Wild-type control:** CDS length 2787 nt; predicted protein 928 aa; start codon ATG; stop codon TGA; Frame 1.

**Documented mutation (c.373G>T):** Mutant CDS length unchanged (2787 nt). Translation produced a real biological protein of 124 amino acids, terminating at the premature stop codon at position 125. Reading frame unaffected. 804 amino acids lost relative to WT.

**Artificial mutation (1-nt deletion, position 151):** Mutant CDS length 2786 nt (no longer divisible by 3). Translation matched WT for the first 50 amino acids, then diverged into a scrambled, frameshifted sequence from position 51 onward, terminating at a premature stop codon at position 64. Real biological protein length: 63 amino acids.

## 7. WT versus Mutant Protein Comparison

Alignment of WT and the corrected (truncated) documented mutant protein showed 100% identity across positions 1–124, with complete absence of the mutant sequence from position 125 onward (805/929 gaps in the raw needle output, reflecting the missing 804 residues). No internal mismatches were present in the aligned region, confirming that the mutation causes a clean truncation rather than any missense change prior to the stop.

| Question | Answer |
|---|---|
| First point of difference | Position 125 |
| Only one amino acid affected? | No — the entire downstream region (804 aa) is absent |
| Multiple downstream aa changed? | Yes, all 804 |
| Deletion or insertion? | Neither — premature termination |
| Premature stop codon? | Yes, at codon 125 |
| Reading frame changed? | No |
| Protein length changed? | Yes: 928 → 124 aa |
| Mutation type | Nonsense |

## 8. Artificial Mutation Experiment

A 1-nucleotide deletion at position 151 (removal of a single G within codon 51) was chosen to contrast a frameshift mutation against the documented nonsense mutation. Because 1 is not divisible by 3, every codon downstream of the deletion was shifted out of its normal reading frame. The resulting protein matched WT for the first 50 residues, then produced a completely different, non-biological amino acid sequence from position 51 to 63, before terminating at a premature stop codon that arose incidentally from the shifted frame rather than from a direct substitution.

| Feature | WT | Documented (Nonsense) | Artificial (Frameshift) |
|---|---|---|---|
| CDS length | 2787 nt | 2787 nt | 2786 nt |
| Divisible by 3? | Yes | Yes | No |
| Protein length | 928 aa | 124 aa | 63 aa |
| Reading frame changed? | — | No | Yes, from codon 51 |
| Premature stop? | — | Codon 125 | Codon 64 |
| Nature of loss | — | Clean truncation | Scrambled sequence, then truncation |

Both mutations destroy protein function completely, but through different mechanisms: the nonsense mutation directly creates a stop codon without disturbing the frame, producing a predictable, clean truncation. The frameshift mutation corrupts every downstream codon, producing meaningless sequence before coincidentally hitting a stop codon at an unpredictable position. This demonstrates that both the type of mutation and whether the number of affected nucleotides is divisible by three determine the severity and predictability of the outcome, independent of where in the gene the change occurs.

## 9. Molecular Interpretation: Gene → Mutation → Protein → Cellular Effect → Phenotype

The c.373G>T substitution converts the glutamate codon at position 125 into a stop codon without altering the reading frame. Translation terminates at residue 124 instead of continuing to residue 928, producing a protein missing roughly 87% of its normal length. This truncation eliminates two functionally essential regions: the pocket domain (~aa 379–792), through which pRB binds E2F transcription factors, and the C-terminal nuclear localization signal (~aa 860–876), required for nuclear import. Without either region, the truncated protein — even if stably produced — could neither reach the nucleus nor repress E2F target genes.

Functionally, this represents a complete loss-of-function allele. Following Knudson's two-hit model, this alone does not cause disease while a normal RB1 allele remains in a cell, since the remaining allele still supplies enough functional pRB to maintain the G1 checkpoint. However, in a person carrying this mutation in the germline, every retinal cell starts out one hit away from total RB1 loss. A second somatic mutation or loss-of-heterozygosity event in even one retinal cell removes the G1 checkpoint entirely in that cell, allowing unchecked progression into S phase and uncontrolled proliferation — the origin of a retinoblastoma tumor.

This mechanism is consistent with the variant's ClinVar classification (Pathogenic/Likely pathogenic) and with RB1's ClinGen designation as having sufficient evidence for dosage pathogenicity.

## 10. Limitations

All conclusions regarding protein truncation, domain loss, and predicted loss of function are based on computational translation of the mutant CDS, not experimental evidence. This predicts what protein sequence would result if the mutant mRNA were translated, but does not confirm that this truncated protein is actually produced, stable, or absent in a real human retinal cell. Nonsense mutations positioned this early in a transcript are frequently subject to nonsense-mediated decay (NMD), a surveillance pathway that degrades transcripts containing premature stop codons before translation produces a stable protein at all. Confirming the true fate of this mutant transcript/protein would require experimental evidence such as Western blotting or mRNA quantification in patient-derived cells. Additionally, exon/domain boundary estimates were drawn from literature and may vary slightly between sources.

## 11. Conclusion

The RB1 c.373G>T (p.Glu125Ter) mutation is a nonsense mutation that introduces a premature stop codon early in the coding sequence, predicted to truncate the RB protein from 928 to 124 amino acids and eliminate both its E2F-binding pocket domain and its nuclear localization signal. This computational analysis, combined with the variant's established pathogenic classification in ClinVar, supports a complete loss-of-function mechanism consistent with Knudson's two-hit model of retinoblastoma tumorigenesis. Comparison with a self-designed frameshift mutation further demonstrated that mutation type and whether the number of affected nucleotides is divisible by three critically determine the predictability and severity of the resulting protein change.

## 12. References

National Center for Biotechnology Information. (n.d.). *RB1 RB transcriptional corepressor 1 [Homo sapiens (human)]* (Gene ID: 5925). U.S. National Library of Medicine. https://www.ncbi.nlm.nih.gov/gene/5925 (Accessed September 15, 2026)

National Center for Biotechnology Information. (n.d.). *Homo sapiens RB transcriptional corepressor 1 (RB1), transcript variant 1, mRNA* (NCBI Reference Sequence No. NM_000321.3). U.S. National Library of Medicine. https://www.ncbi.nlm.nih.gov/nuccore/NM_000321.3 (Accessed September 15, 2026)

National Center for Biotechnology Information. (n.d.). *Retinoblastoma-associated protein isoform 1 [Homo sapiens]* (NCBI Reference Sequence No. NP_000312.2). U.S. National Library of Medicine. https://www.ncbi.nlm.nih.gov/protein/NP_000312.2 (Accessed September 15, 2026)

National Center for Biotechnology Information. (n.d.). *NM_000321.3(RB1):c.373G>T (p.Glu125Ter)* (ClinVar Variation ID No. 1334098, Accession No. VCV001334098.5). U.S. National Library of Medicine. https://www.ncbi.nlm.nih.gov/clinvar/variation/1334098/ (Accessed September 15, 2026)

Clinical Genome Resource. (n.d.). *RB1 gene dosage sensitivity curation*. https://search.clinicalgenome.org/kb/genes/HGNC:9884 (Accessed September 15, 2026)
