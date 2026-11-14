# Module 7 Fast Lesson (4.4, 4.5, 4.6)

## 4.4 Validation, retry and feedback loops for extraction

**Exam rule:** Retry only when the model made a format or structure mistake. Send back the document, the failed result and the specific error.

- Pick: follow-up request with original document + failed extraction + exact validation error.
- Reject: "try again" with no detail, or re-sending the same prompt.
- Do not retry when the information is not in the source (for example it sits in another document that was not provided).
- Tool use removes syntax errors. It does not remove semantic errors (items do not sum to total, value in wrong field).
- `calculated_total` next to `stated_total` exposes a mismatch. A `conflict_detected` boolean flags a source that contradicts itself.
- `detected_pattern` on each finding lets you see which patterns developers dismiss.

**Example:** Items sum to $210, total says $250. Retry message names that exact gap.

Trap: "retry up to N times" offered for absent information.

## 4.5 Efficient batch processing

**Exam rule:** Message Batches API = 50% cheaper, up to 24 hours, no latency guarantee. Use it only when nobody is waiting.

- Pick batch: overnight reports, weekly audits, nightly test generation.
- Pick synchronous: pre-merge checks and anything that blocks a person.
- Batch cannot run a tool mid-request and return the result. No multi-turn tool loop inside one request.
- `custom_id` matches each result to its request. Results may arrive in a different order.
- On failures, resubmit only the failed `custom_id`s, fixed (for example split long documents).
- SLA maths: worst case is 24 hours in batch. Submit often enough that 24 + gap fits the SLA. A 30-hour SLA means gaps of 6 hours or less (the guide uses 4).
- Test the prompt on a small sample before the full batch.

Trap: "batch everything to save money".

## 4.6 Multi-instance and multi-pass review

**Exam rule:** The session that wrote the output is a weak reviewer. Use a fresh, independent instance that sees only the output.

- Why self-review is weak: the model keeps its own reasoning and rarely questions it.
- Reject: "review your work" in the same session, or extended thinking in the same session.
- Big reviews: one pass per file for local issues, plus one separate cross-file pass for data flow between files.
- One giant pass causes thin attention and contradictory findings.
- Ask the verifier for a confidence value with each finding. Route low-confidence ones to an extra check or human. Do not just drop them.

**Example:** 40-file PR = 40 file passes + 1 integration pass.

Trap: "more thinking in the same session".
