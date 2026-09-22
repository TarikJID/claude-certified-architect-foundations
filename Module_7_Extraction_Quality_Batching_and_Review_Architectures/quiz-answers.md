# Module 7 — Quiz answers

> Held separately from `quiz.md` on purpose: so a tutor asking a question does
> not have the answer sitting in its context. Attempt first.

## Quiz — Lesson 4.4 (Validation, Retry, and Feedback Loops)

**Q1.** It should append the *specific* validation errors found, alongside the original
document and the failed extraction, so the model sees exactly what was wrong.
Simply re-asking gives the model no concrete feedback to correct against, so it
may repeat the same mistake.

**Q2.** Whether the due date actually exists anywhere in the source document provided.
If it's genuinely absent from the source, retrying is ineffective — no amount of
retrying conjures information the model was never given. Retry only helps for
format/structural errors, not missing source information.

**Q3.** It records which specific code construct or pattern triggered each finding,
turning individual findings into aggregable data. Tracking which
`detected_pattern` values correlate with developer dismissals enables systematic
analysis of which patterns generate false positives — pointing at what to refine.

**Q4.** It catches semantic errors like line items not summing to the stated total. The
model extracts `stated_total` (what the document claims) and derives
`calculated_total` from the line items it also extracted; a downstream
comparison of the two automatically flags a discrepancy.


## Quiz — Lesson 4.5 (Batch Processing Strategies)

**Q1.** No — the Batches API gives no latency SLA (up to 24 hours) and is meant for
non-blocking, latency-tolerant workloads. A pre-merge check is a blocking
workflow and must use the synchronous Messages API despite its higher per-token
cost.

**Q2.** Each batch entry is one independent request processed once, returning one
result — there's no mechanism to pause an entry mid-processing, execute a
client-side tool call, and feed the result back into that same request before it
completes. A full agentic tool-use loop requires multiple turns.

**Q3.** `custom_id` — every batch request/result pair is tagged with the caller-supplied
`custom_id`. Look up the 40 `custom_id`s of the `errored` results, apply any
needed fix (e.g. chunking oversized documents), and resubmit only that subset
rather than the whole batch.

**Q4.** At least every 6 hours. General formula: to guarantee results within N hours,
submit batches at an interval no longer than (N − 24) hours, since any individual
request might sit for the full 24-hour window in the worst case.

**Q5.** A failed or low-quality large-scale batch run is expensive to detect and re-run.
Iterating on prompt quality against a small sample first catches format issues,
false positives, and edge-case failures cheaply, maximizing the batch's
first-pass success rate.


## Quiz — Lesson 4.6 (Multi-Instance and Multi-Pass Review)

**Q1.** The session retains the reasoning context and assumptions that led to its
original choices, making it structurally less likely to question its own
decisions than a reviewer encountering the output fresh — it tends to re-justify
what it already committed to.

**Q2.** No — extended thinking still happens within the same request/response turn and
the same conversational context as the original generation, so it's still
anchored by the model's own prior generation choices. It's not a substitute for
an independent reviewer with no memory of that reasoning.

**Q3.** 40 focused single-file passes (each looking only at that file's local logic) plus
one separate cross-file integration pass dedicated to tracing how data flows
between the changed files — rather than one pass attempting both at once.

**Q4.** It enables calibrated routing: high-confidence findings can be surfaced directly,
while low-confidence findings can be routed to an additional check (another pass
or a human) instead of being silently dropped or given the same authority as a
high-confidence finding.
