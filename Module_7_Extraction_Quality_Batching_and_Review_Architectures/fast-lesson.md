# Module 7 Fast Lesson (4.4, 4.5, 4.6)

## 4.4 Checking and retrying extraction results

**Setting:** A company uses Claude to read invoices and fill in a fixed form (vendor, line items, total): this is *extraction*, and the form's rulebook is the *schema*. A *validation* step checks the filled form. Sometimes numbers do not add up.

**Before:** The check fails; the system says only "try again".
**After:** Send back the invoice, Claude's first answer and the exact problem: "items add up to $210 but total says $250".

**Exam rule:** Retry with the specific error, only if the answer is in the document.

- Trap: a bare "try again" gives Claude nothing to fix.
- If the due date sits in a separate document Claude never received, retrying cannot help. Trap: "retry 5 times" repeats the gap. Allow an empty value or supply the document.
- *Tool use* (Claude fills the form through a defined tool) stops broken formatting, not wrong values: wrong sums, values in wrong fields.
- Ask for `stated_total` (what the invoice says) and `calculated_total` (Claude's own sum); a mismatch flags itself. A `conflict_detected` yes/no field shows when the invoice contradicts itself.
- Separate setting: developers dismiss many comments from a code-review bot (a program where Claude comments on code automatically). A `detected_pattern` field records what triggered each, showing which kinds get dismissed.

## 4.5 Batch processing: cheap but slow

**Setting:** The same company processes 50,000 invoices nightly; nobody reads results until morning. Two ways to send work: *Synchronous*: one request, answer in seconds. The *Message Batches API* (Claude's bulk service): many requests at once, 50% cheaper, but up to 24 hours, no promised speed.

**Before:** Synchronous, full price.
**After:** One batch at half price, still ready by morning.

**Exam rule:** Use batch only when nobody is waiting for the answer.

- Separate setting: a check that locks a developer's merge button (which adds his change to the main code) must be synchronous. Trap: "batch everything to save money" leaves him waiting hours.
- A batch request cannot pause, let your code run a tool (e.g. a database lookup), and continue. Lookup rounds do not fit.
- Each request carries a `custom_id` (your own label); results return in any order, matched by label. If 40 fail for being too long, resubmit only those, split smaller. Trap: resubmitting all 50,000 pays twice.
- Deadline maths: waiting for the next submission, plus up to 24 hours. A 30-hour promise needs a batch every 6 hours or less (the guide uses 4).
- Test the prompt (Claude's written instructions) on about 20 invoices synchronously first. Trap: a mistake found at the end means rerunning everything.

## 4.6 Who reviews the work, and in how many passes

**Setting:** A team's automatic system uses Claude to write code and review pull requests (proposed code changes). A *session* is one conversation; an *instance* is a separate Claude call starting fresh. Problem: reviews miss subtle bugs.

**Before:** The writing session is asked "review your code". It finds nothing.
**After:** A fresh instance, given only code and review rules, spots the flaw.

**Exam rule:** The writer is a weak reviewer. Use an independent one; split big reviews.

- The writer still holds its own reasoning, so it defends its choices.
- Trap: "think harder" using *extended thinking* (Claude reasons step by step first) in the same session. Same blind spot.
- 40-file change: one pass (one review run) per file for bugs inside that file, plus a separate pass for how data moves between files. Trap: one giant pass spreads attention thin and contradicts itself (flags a pattern in file 3, accepts it in file 17).
- Per-file passes miss file B breaking after file A changed; the cross-file pass catches it.
- The checker gives each finding (reported problem) a confidence score: how sure it is the problem is real. Post high ones; send low ones to another check or a person. Trap: deleting low ones loses real problems.
