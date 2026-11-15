# Module 7 Fast MCQ (4.4, 4.5, 4.6)

Pick the single best answer. No answers in this file.

---

## 4.4 Checking and retrying extraction results

### Q4.4-1 [4.4]
A company uses Claude to read invoices and fill in a fixed form (vendor, line items, total). An automatic check then adds up the line items Claude filled in and compares the sum with the total Claude filled in. On one invoice the line items add up to $210, but the total says $250. The invoice itself is clear and shows the correct numbers. Deciding constraint: the information needed is in the invoice, so a second attempt can fix it. How should the second attempt be set up?

- A. Send the same request again, unchanged, and hope the answer differs.
- B. Send the invoice, Claude's first answer, and a note saying the line items add up to $210 but the total says $250.
- C. Send only the note "Your previous answer was wrong, try again."
- D. Switch to a larger Claude model and send the same request, unchanged.

### Q4.4-2 [4.4]
The same invoice system must fill in a "due date" field (the day payment is due). For 300 invoices the field comes back empty. On those invoices the only mention is "payment terms are in purchase order PO-77". PO-77 is a separate document that is never sent to Claude. Deciding constraint: the due date does not appear anywhere in what Claude receives. What is the best response?

- A. Retry each invoice up to five times, telling Claude each time that the due date is missing.
- B. Retry each invoice with a setting that forces Claude to always put a date in the field.
- C. Add three worked examples to the instructions showing due dates being found on other invoices.
- D. Stop retrying. Let the field stay empty for these invoices, and get the PO-77 document added to what Claude receives.

### Q4.4-3 [4.4]
The invoice system uses tool use: Claude fills in the form through a defined tool, so the output always has the right fields and the right kinds of value (numbers where numbers belong). Every output is well formed. But on about 3% of invoices, the line items Claude filled in do not add up to the total it filled in. Deciding constraint: the form is always well formed, so the problem is wrong values, not broken formatting. What is the best design response?

- A. Treat it as a wrong-values problem. Have Claude fill in both the total printed on the invoice and its own sum of the line items, so any difference is flagged automatically.
- B. Treat it as a formatting problem. Make the form's rules stricter so the totals have to match.
- C. Treat it as a formatting problem. Add a step that repairs broken output.
- D. Treat it as a wrong-values problem. Let Claude answer in free text instead of through the form, so it can reconsider.

### Q4.4-4 [4.4]
A team runs a code-review bot: Claude reads each proposed code change and posts comments about possible problems. Developers can dismiss (reject) a comment they think is wrong. Many comments are being dismissed. Deciding constraint: the team wants data showing which kinds of comment get dismissed most, so they know which part of the instructions to fix. What should they add?

- A. An instruction telling Claude to post only comments it is highly confident about.
- B. A weekly meeting where developers recall from memory which comments they dismissed.
- C. A field on every comment that records which code pattern triggered it, stored together with whether the developer dismissed it.
- D. A longer instruction listing every kind of code Claude might see.

### Q4.4-5 [4.4]
The extraction system also reads contracts. One scanned contract says the total is $12,000 on page 1 and $11,400 on page 4. Claude read both pages correctly; the document itself disagrees with itself. Deciding constraint: a person downstream must be able to see that the document is inconsistent. Which form design is best?

- A. Always keep the first total found and ignore any later one.
- B. Record both values and add a yes/no field "conflict detected", set to yes, so the inconsistency is visible.
- C. Retry the extraction until both totals match.
- D. Make "total" a field that must always hold exactly one value, so Claude has to pick.

---

## 4.5 Batch processing: cheap but slow

### Q4.5-1 [4.5]
Claude can be called two ways. Synchronous: one request, answer in seconds, full price. The Message Batches API: many requests sent together, 50% cheaper, but results can take up to 24 hours and no speed is promised. A team has two jobs. Job 1: a check on every code change that keeps the developer's merge button (which adds his change to the main code) locked until the check finishes. Job 2: a weekly audit of 10,000 documents that nobody reads until Monday. Deciding constraint: in Job 1 a person is waiting; in Job 2 nobody is. Which assignment is best?

- A. Batch for both jobs, to save the most money.
- B. Synchronous for both jobs, to keep things simple.
- C. Synchronous for Job 1, batch for Job 2.
- D. Batch for Job 1, synchronous for Job 2.

### Q4.5-2 [4.5]
A team wants to move an overnight support-ticket job to the Message Batches API (cheap, slow, many requests sent together). In the job, for each ticket Claude asks for a database lookup, the team's own code runs the lookup and hands back the answer, Claude reads it and asks for the next lookup, several rounds per ticket. Deciding constraint: each ticket needs several back-and-forth lookup rounds before Claude can finish. What is the main obstacle?

- A. A batch request cannot pause halfway, let the team's code run the lookup, and continue, so the back-and-forth rounds cannot happen inside one batch request.
- B. Batch requests cannot mention any tools at all.
- C. Lookups inside a batch are charged at full price, which removes the saving.
- D. Batches are limited to one hour, which is too short for lookups.

### Q4.5-3 [4.5]
A batch of 10,000 documents has finished. Each request was sent with a "custom_id", a unique label the team chose, and each result comes back carrying the same label. Results come back in a different order from the one they were sent in. 40 results failed because those documents were too long for Claude to read in one go. Deciding constraint: the team must fix exactly the failed documents without paying for the rest again. What is the best next step?

- A. Resend all 10,000 documents to be safe.
- B. Match results to requests by their position in the results list, then resend the 40 unchanged.
- C. Give up on the 40 documents.
- D. Use the labels to find the 40 failed documents, split each into smaller pieces, and resend only those.

### Q4.5-4 [4.5]
Support tickets arrive at any time. The business promises a result within 30 hours of a ticket arriving. Tickets are collected and sent as a batch on a fixed schedule; a batch can take up to 24 hours to finish. Deciding constraint: a ticket may arrive just after a batch was sent, so it waits for the next one and then may take the full 24 hours. Which schedule keeps the 30-hour promise?

- A. Send a batch every 24 hours.
- B. Send a batch every 4 hours.
- C. Send a batch every 12 hours.
- D. Send a batch every 30 hours.

### Q4.5-5 [4.5]
A team will extract data from 50,000 documents using the Message Batches API (cheap, slow, many requests together). The instructions they wrote for Claude have never been tried on real documents. Deciding constraint: any mistake in the instructions will repeat across every document it runs on. What is the most efficient approach?

- A. Send all 50,000 now and fix problems after the batch finishes.
- B. Send 50 batches of 1,000 and fix problems after each one finishes.
- C. Try the instructions on about 20 typical documents with fast single requests, fix what goes wrong, then send the full batch.
- D. Skip testing; the 50% discount will cover any reruns.

---

## 4.6 Who reviews the work, and in how many passes

### Q4.6-1 [4.6]
In one conversation (session), Claude wrote a login-checking function. In that same conversation, the developer then asked "Review your code for bugs." Claude found none. A subtle flaw was later found by users. Deciding constraint: the reviewer was the same conversation that made the design choices. What best explains the missed flaw?

- A. The review should have used a stricter output form so the findings (reported problems) were neatly formatted.
- B. The review request was too short.
- C. Code review only works when run through the cheap, slow batch service.
- D. The conversation still held its own reasoning behind the design choices, so it was unlikely to question them.

### Q4.6-2 [4.6]
A team has Claude write code and wants the best chance of catching subtle bugs before the code is accepted. Deciding constraint: the reviewer must not be influenced by the reasoning that produced the code. Which design is best?

- A. In the same conversation, switch on extended thinking (Claude reasons step by step before answering) and say "think hard and double-check your work".
- B. Send only the finished code and the review rules to a new, separate Claude call that never saw the writing conversation.
- C. Ask the same conversation to review its code twice.
- D. Add "be careful and only report issues you are sure about" to the original writing instructions.

### Q4.6-3 [4.6]
A proposed code change touches 40 files. One review run (pass) over all 40 at once gives shallow comments, and it calls a pattern in file 3 a problem while accepting the same pattern in file 17. Deciding constraint: the redesign must give each file focused attention and still catch problems that cross between files. What is the best redesign?

- A. One focused pass per file for problems inside that file, plus one separate pass only for problems between files.
- B. Keep one pass but write longer instructions.
- C. One pass per file, and nothing else.
- D. Split the files at random into four groups of ten, one pass per group.

### Q4.6-4 [4.6]
A checking step re-examines the comments a code-review bot wants to post. The team wants strong comments posted straight away, doubtful ones checked again, and nothing silently thrown away. A confidence score means how sure the checker is that a comment points to a real problem. Deciding constraint: the system must be able to tell strong comments from doubtful ones. What should the checking step produce?

- A. A list where every comment below a fixed score is deleted.
- B. A plain yes/no for each comment, with every "yes" posted the same way.
- C. A confidence score with each comment, so high-scoring ones are posted and low-scoring ones go to another check or a person.
- D. A confidence score given by the conversation that wrote the code, about its own code.

### Q4.6-5 [4.6]
A code change edits a function in file A so that it now hands back its data in a different shape. A part of file B that uses that function now breaks. Each file was reviewed in its own separate pass, and the break was missed. Deciding constraint: the problem only shows when files A and B are looked at together. Which addition would catch this kind of problem?

- A. Longer, more detailed instructions for each per-file pass.
- B. Extended thinking (step-by-step reasoning) switched on inside each per-file pass.
- C. Asking each per-file pass to re-check its own comments.
- D. A separate pass whose only job is following data between files.
