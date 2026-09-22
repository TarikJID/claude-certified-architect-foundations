# Module 10 — Quiz answers

> Held separately from `quiz.md` on purpose: so a tutor asking a question does
> not have the answer sitting in its context. Attempt first.

## Quiz — Lesson 5.5 (Human Review and Confidence Calibration)

**Q1.** Not necessarily safe. The aggregate figure can mask much worse performance on a
specific document type or field segment. You must validate accuracy broken down
by document type and field before reducing review, since errors tend to cluster
in specific segments rather than spreading evenly.

**Q2.** It misses the case where the model develops a new failure mode that happens to
produce high, but wrong, confidence. Stratified random sampling — drawing from
each stratum (document type, confidence band, field type) including
high-confidence extractions — is needed to catch that.

**Q3.** Raw model-reported confidence is not automatically a calibrated probability — the
same 0.9 score means different actual correctness rates for different fields.
The score must be calibrated against a labeled validation set per field, and
review thresholds set based on that measured relationship, not the raw number.

**Q4.** (b) — routing should prioritize extractions that most need attention. Low
confidence combined with ambiguous/contradictory source documents is a stronger
signal of an untrustworthy extraction than low confidence alone, so it should be
routed ahead of (a).


## Quiz — Lesson 5.6 (Information Provenance and Multi-Source Synthesis)

**Q1.** Source attribution loss during summarization — the summarizer merged
similar-sounding claims from different sources, discarding which source said
what. The fix: require subagents to output structured claim-source mappings
(claim, source, excerpt) and require the synthesis agent to preserve and merge
those mappings, not just the claims.

**Q2.** It should preserve both values with source attribution, explicitly annotated as
conflicting, and let the coordinator or downstream decision-maker decide how to
reconcile them. It should NOT silently pick one value, which discards
information and can be wrong.

**Q3.** Without dates, this could be misread as two sources disagreeing about the same
current number (a contradiction). Requiring subagents to include the publication
or data-collection date of each source lets a downstream synthesis step
correctly interpret this as temporal change (growth over three years) instead.

**Q4.** Use explicit separate sections — e.g. "Well-established findings" versus
"Contested / single-source findings" — preserving each source's own
characterization and methodological context, rather than presenting both kinds
of claim with the same tone and certainty in undifferentiated prose.

**Q5.** No — each content type should be rendered in the format it's naturally
structured for: revenue figures as a table, the narrative as prose, and
compliance requirements as a structured/numbered list. Forcing everything into
one uniform format typically loses information the natural format would have
preserved and reads worse.
