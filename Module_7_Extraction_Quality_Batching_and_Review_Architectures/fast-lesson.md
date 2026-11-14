# Module 7 Fast Lesson (4.4, 4.5, 4.6)

## 4.4 Validation, retry and feedback loops for extraction

**Exam rule:** Retry only fixes format or structure mistakes. Send back the document, the failed result and the specific error.

- Pick: follow-up with original document, failed extraction and exact validation error. Reject: "try again" or the same prompt.
- No retry when the information is absent from the source (for example it sits in a document not provided).
- Tool use removes syntax errors, not semantic ones (items do not sum to total, value in wrong field).
- `calculated_total` beside `stated_total` exposes a mismatch. `conflict_detected` flags a source that contradicts itself.
- `detected_pattern` on each finding shows which patterns developers dismiss.

**Example:** Items sum to $210, total says $250. The retry names that gap.

Trap: "retry up to N times" for absent information.

## 4.5 Efficient batch processing

**Exam rule:** Message Batches API = 50% cheaper, up to 24 hours, no latency guarantee. Use it only when nobody is waiting.

- Pick batch: overnight reports, weekly audits, nightly test generation. Pick synchronous: pre-merge checks and anything blocking a person.
- Batch cannot run a tool mid-request and return the result. No multi-turn tool loop in one request.
- `custom_id` matches results to requests (order may differ). Resubmit only failed ones, fixed (for example split long documents).
- SLA maths: worst case is 24 hours in batch. 24 + submission gap must fit the SLA. A 30-hour SLA needs gaps of 6 hours or less (the guide uses 4).
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
