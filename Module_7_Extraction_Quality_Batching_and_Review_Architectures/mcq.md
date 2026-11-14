# Module 7 Fast MCQ (4.4, 4.5, 4.6)

Pick the single best answer. No answers in this file.

---

## 4.4 Validation, retry and feedback loops

### Q4.4-1 [4.4]
An invoice extraction uses tool use with a JSON schema. A validation step finds that the extracted line items add up to $210, but the extracted total is $250. The invoice text is available and clearly shows the correct values. How should the retry be designed?

- A. Send the same extraction prompt again unchanged and hope the output differs.
- B. Send the original invoice, the first extraction, and a message stating that the line items sum to $210 but the total is $250.
- C. Send only the message "Your previous answer was wrong, try again."
- D. Switch to a larger model and send the same prompt unchanged.

### Q4.4-2 [4.4]
A pipeline extracts `due_date` from invoices. For 300 invoices the field comes back empty. A review shows these invoices only say "payment terms are in purchase order PO-77", and PO-77 is a separate document that is never given to the model. What is the best response?

- A. Retry each invoice up to five times, adding the validation error each time.
- B. Retry each invoice with `tool_choice` set to "any".
- C. Add three few-shot examples showing due dates being extracted.
- D. Do not retry. Allow a null value for these invoices and supply or request the missing PO document.

### Q4.4-3 [4.4]
Extraction uses tool use with a strict JSON schema. Every output is valid JSON with correct field types. But about 3% of outputs have line items that do not add up to the stated total. What kind of error is this, and what is the best design response?

- A. A semantic error. Extract both `stated_total` and `calculated_total` so a mismatch is flagged automatically.
- B. A syntax error. Make the schema stricter so the totals must match.
- C. A syntax error. Add a step that repairs broken JSON.
- D. A semantic error. Change `tool_choice` to "auto" so the model can reconsider.

### Q4.4-4 [4.4]
An automated code reviewer posts findings. Developers dismiss many of them. The team wants to learn which kinds of finding are mostly dismissed, so they can fix the prompt. What should they add?

- A. An instruction telling the model to report only findings it is highly confident about.
- B. A weekly meeting where developers describe dismissed findings from memory.
- C. A `detected_pattern` field on every finding, recorded together with whether the developer dismissed it.
- D. A longer system prompt listing every possible code construct.

### Q4.4-5 [4.4]
A scanned contract states a total of $12,000 on page 1 and a different total of $11,400 on page 4. The extraction tool must handle documents like this. Which schema design is best?

- A. Always keep the first total found and ignore later ones.
- B. Return both values and add a `conflict_detected` boolean set to true, so the inconsistency is visible.
- C. Retry the extraction until both totals match.
- D. Mark `total` as a required field so the model must decide.

---

## 4.5 Efficient batch processing

### Q4.5-1 [4.5]
A team has two jobs. Job 1: a check that runs on every pull request and blocks the merge button until it finishes. Job 2: a weekly audit of 10,000 documents that nobody reads until Monday. The Message Batches API gives a 50% discount, can take up to 24 hours, and has no guaranteed latency. Which assignment is best?

- A. Batch API for both jobs, to maximise savings.
- B. Synchronous API for both jobs, to keep things simple.
- C. Synchronous API for Job 1, Batch API for Job 2.
- D. Batch API for Job 1, synchronous API for Job 2.

### Q4.5-2 [4.5]
A team wants to move an overnight workflow to the Batches API. In the workflow, Claude calls a lookup tool, the team's own code runs the lookup, Claude reads the result and decides on the next lookup, and this repeats several times per ticket. What is the main obstacle?

- A. A batch request cannot pause to run a tool and feed the result back into the same request, so the multi-turn tool loop cannot complete inside one batch entry.
- B. Batch requests cannot include a `tools` list at all.
- C. Tool calls are charged at full price inside batches, which removes the saving.
- D. Batches are limited to one hour, which is too short for tool calls.

### Q4.5-3 [4.5]
A batch of 10,000 documents finishes. Each request was submitted with a unique `custom_id`. Results come back in a different order from submission. 40 results show an error because those documents were longer than the context limit. What is the best next step?

- A. Resubmit all 10,000 documents to be safe.
- B. Match results to requests by their position in the output, then resubmit the 40 unchanged.
- C. Discard the 40 documents as unprocessable.
- D. Use the `custom_id` values to find the 40 failed requests, split those documents into smaller chunks, and resubmit only them.

### Q4.5-4 [4.5]
Support tickets arrive at any time. The business promises results within 30 hours of arrival. A batch can take up to 24 hours to process in the worst case. Assume a ticket may arrive just after a batch was submitted. Which submission schedule guarantees the 30-hour promise?

- A. Submit a batch every 24 hours.
- B. Submit a batch every 4 hours.
- C. Submit a batch every 12 hours.
- D. Submit a batch every 30 hours.

### Q4.5-5 [4.5]
A team will extract data from 50,000 documents using the Batches API. The extraction prompt has never been run on real documents. What is the most efficient approach?

- A. Submit all 50,000 now and fix problems after the batch finishes.
- B. Submit 50 batches of 1,000 and fix problems after each finishes.
- C. Run the prompt synchronously on a small sample of about 20 representative documents, fix the problems found, then submit the full batch.
- D. Skip testing and rely on the 50% discount to absorb any reruns.

---

## 4.6 Multi-instance and multi-pass review

### Q4.6-1 [4.6]
In one session, Claude wrote an authentication function. In the same session, the developer asked "Review your code for bugs." Claude found none. A subtle flaw was found later in production. What best explains the missed flaw?

- A. The review needed a different `tool_choice` setting.
- B. The review prompt was too short.
- C. Code review only works when run through the Batches API.
- D. The session still held the reasoning behind its own design choices, so it was less likely to question them.

### Q4.6-2 [4.6]
A team generates code with Claude and wants the best chance of catching subtle issues before merge. Which design is best?

- A. In the same session, add "think hard and double-check your work" with extended thinking.
- B. Send only the final code and the review criteria to a fresh Claude instance that never saw the generating session.
- C. Ask the same session to review its code twice.
- D. Add "be conservative and only report high-confidence issues" to the generating prompt.

### Q4.6-3 [4.6]
A pull request changes 40 files. A single review pass over all of them gives shallow comments, and it flags a pattern in file 3 as a problem but accepts the same pattern in file 17. What is the best redesign?

- A. One focused pass per file for local issues, plus a separate pass dedicated to cross-file issues.
- B. Keep one pass but use a longer prompt.
- C. Per-file passes only, with no other pass.
- D. Split the files at random into four groups of ten and review each group in one pass.

### Q4.6-4 [4.6]
A verification pass reviews findings from a code reviewer. The team wants strong findings posted right away, weak findings checked further, and nothing silently lost. What should the verification pass produce?

- A. A finding list where everything below a fixed score is deleted.
- B. A flag or no-flag decision only, with all flagged findings posted equally.
- C. A confidence value with each finding, so high-confidence findings are posted and low-confidence ones go to an extra check or a human.
- D. A confidence value reported by the generating session about its own code.

### Q4.6-5 [4.6]
A changed function in file A now returns a different data shape. A caller in file B breaks. A per-file review of each file separately missed it. Which addition would catch this kind of issue?

- A. Longer, more detailed per-file prompts.
- B. Extended thinking switched on inside each per-file pass.
- C. Asking each per-file pass to self-review its findings.
- D. A separate integration pass dedicated to data flow across files.
