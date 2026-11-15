# Module 7 Fast Lesson (4.4, 4.5, 4.6)

## 4.4 Checking and retrying extraction results

**Setting:** A company uses Claude to read invoices and fill in a fixed form: vendor, line items, total. This is *extraction*. The form's rulebook is the *schema*. A *validation* step checks the filled form. Sometimes numbers do not add up.

**Before:** The check fails; the system says only "try again". Claude guesses again.
**After:** Send back the invoice, Claude's first answer and the exact problem: "items add up to $210 but total says $250".

**Exam rule:** Retry with the specific error, only if the answer is in the document.

- Pick the "after" retry. Trap: a bare "try again" gives Claude nothing to fix.
- If the due date sits in a separate document Claude never received, retrying cannot help. Trap: "retry 5 times" repeats the gap. Allow an empty value or supply the document.
- *Tool use* (Claude fills the form through a defined tool) stops broken formatting, not wrong values: a wrong sum, or a value in the wrong field.
- Ask for `stated_total` (what the invoice says) and `calculated_total` (Claude's own sum); a mismatch flags itself. A `conflict_detected` yes/no field shows when the invoice contradicts itself.
- Separate setting: developers often dismiss a code-review bot's comments. A `detected_pattern` field records what triggered each one, showing which kinds get dismissed.

## 4.5 Batch processing: cheap but slow

**Setting:** The same company processes 50,000 invoices nightly; nobody reads results until morning. Two ways to send work: *Synchronous*: one request, answer in seconds. The *Message Batches API*: many requests at once, 50% cheaper, but up to 24 hours, with no promised speed.

**Before:** The nightly job runs synchronously at full price.
**After:** One batch at half price, still ready by morning.

**Exam rule:** Use batch only when nobody is waiting for the answer.

- Separate setting: a check that blocks a developer's merge button must be synchronous. Trap: "batch everything to save money" leaves him waiting hours.
- A batch request cannot pause, let your code run a tool (such as a database lookup), and continue. Work needing several lookup rounds does not fit.
- Each request carries a `custom_id` (your own label); results return in any order; the label matches them. If 40 fail for being too long, resubmit only those, split smaller. Trap: resubmitting all 50,000 pays twice.
- Deadline maths: up to 24 hours in the batch, plus waiting for the next submission. A 30-hour promise needs a batch every 6 hours or less (the guide uses 4).
- Test the prompt synchronously on about 20 invoices first. Trap: a mistake found at the end means rerunning all 50,000.

## 4.6 Who reviews the work, and in how many passes

**Setting:** A team's automatic checking system uses Claude to write code and review pull requests (proposed code changes). A *session* is one conversation; an *instance* is a separate Claude call starting fresh. Problem: reviews miss subtle bugs.

**Before:** The writing session is asked "review your code". It finds nothing.
**After:** A fresh instance gets only the code and review rules, and spots the flaw.

**Exam rule:** The writer is a weak reviewer. Use an independent one; split big reviews.

- The writing session still holds its own reasoning, so it defends rather than questions its choices.
- Trap: "think harder" using *extended thinking* (Claude reasons step by step before answering) in the same session. Same session, same blind spot.
- 40-file change: one pass (one review run) per file for local bugs, plus a separate pass for how data moves between files. Trap: one giant pass spreads attention thin and contradicts itself (flags a pattern in file 3, accepts it in file 17).
- Per-file passes alone miss file B breaking because file A changed. The cross-file pass catches it.
- The checker gives a confidence score per finding. Post high ones; send low ones to another check or a person. Trap: deleting low ones silently loses real problems.
