# Module 10 Fast Lesson

## 5.5 Human review and confidence calibration

**Exam rule:** One overall accuracy number can hide a bad segment. Check accuracy per document type and per field before you cut human review.

- Pick: accuracy broken down by document type and field.
- Pick: a random sample from each segment, including high-confidence items (stratified random sampling).
- Pick: field-level confidence, checked against a labeled validation set. Set thresholds from measured correctness.
- Pick: send to a human when calibrated confidence is low, or when the source is ambiguous or self-contradictory. Contradictory plus low confidence goes first.
- Reject: "97% overall, so automate."
- Reject: "review only the low-confidence items." New failures hide in confident wrong answers.
- Reject: "0.9 confidence means 90% correct." Raw scores are not calibrated.

Example: 97% overall hides handwritten receipts at 60%. Keep review for receipts only.

## 5.6 Provenance and uncertainty in multi-source synthesis

**Exam rule:** Keep every claim tied to its source, through every step. When sources disagree, show both values, do not pick one.

- Pick: subagents output structured claim-source mappings (claim, source, excerpt). Synthesis keeps them. The citations feature does this.
- Pick: keep both conflicting numbers, with sources, marked as conflicting. The coordinator or reader decides.
- Pick: include a publication or collection date with each figure. Different dates may be change over time, not conflict.
- Pick: separate "well-established" from "contested or single-source" sections.
- Pick: tables for numbers, prose for narrative, lists for technical items.
- Reject: summaries that merge claims, averaging, or silently choosing the newest or biggest number.
- Reject: one format for everything.

Example: 500 staff (2023) and 1,200 staff (2026) is growth, not a conflict.
