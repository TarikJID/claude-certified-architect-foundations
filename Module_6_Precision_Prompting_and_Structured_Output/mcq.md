# Module 6 MCQ Practice (questions only)

Pick the single best answer for each question.

---

## Task 4.1

### Q4.1-1 [4.1]
A code review tool checks comments in pull requests. Its prompt says "Check that comments are accurate." Developers report that most of its comment findings are wrong or trivial. Which prompt change most improves precision?

A. Add "Be conservative and only report findings you are highly confident about."
B. Add "Be thorough and report every possible comment issue so nothing is missed."
C. Replace it with "Flag a comment only when the behavior it claims contradicts what the code actually does."
D. Ask the model to give each finding a confidence score from 1 to 10 and then ignore low scores.

### Q4.1-2 [4.1]
An automated reviewer reports three categories: bugs, security, and minor style. Reviewers measured that bugs and security findings are almost always correct, but about 45% of style findings are wrong. Developers have started skimming all comments, including security ones. What is the best action?

A. Keep all three categories and add a note saying some findings may be inaccurate.
B. Lower the confidence cutoff for every category so fewer findings appear.
C. Switch the reviewer off completely until it is perfect.
D. Temporarily disable the style category, keep bugs and security, and improve the style prompt before re-enabling it.

### Q4.1-3 [4.1]
A reviewer rates severity as critical, high, medium, or low. The prompt only gives each level a name. The same unhandled null value that crashes a request is labeled "critical" in one run and "medium" in another. What is the best fix?

A. Give each severity level a concrete code example of an issue that belongs at that level.
B. Add the sentence "Be consistent when assigning severity."
C. Add more severity levels so each issue has a closer match.
D. Run the review twice and always keep the higher severity.

### Q4.1-4 [4.1]
A team wants a review prompt that reports bugs and security problems but ignores minor style issues and patterns that are normal in their codebase. Which prompt wording best achieves this?

A. "Only report findings when you are very sure they matter."
B. "Report bugs and security issues. Do not report minor style issues or local team patterns."
C. "Report every issue you find and mark how confident you are in each."
D. "Be conservative and avoid nitpicking."

### Q4.1-5 [4.1]
In one tool, security findings are correct 95% of the time, and naming-style findings are correct 40% of the time. A lead notices developers now ignore real security findings. Which explanation fits best?

A. The security prompt is probably broken and needs a rewrite.
B. Developers prefer style feedback and dislike security feedback.
C. Noisy style findings made developers distrust the whole tool, including the accurate security category.
D. The model is less confident about security findings than about style findings.

---

## Task 4.2

### Q4.2-1 [4.2]
A prompt describes in detail that each finding must have a location, an issue, a severity, and a suggested fix. The output still varies: some findings drop fields and the phrasing changes each time. What is the most effective next step?

A. Rewrite the instructions to be longer and more detailed.
B. Add two or three fully worked example findings that show all four fields in the exact format wanted.
C. Add "Always use the same format" in capital letters.
D. Only accept findings the model marks as high confidence.

### Q4.2-2 [4.2]
An agent has two tools: search_web (searches the public internet) and search_docs (searches the company's internal documents). Requests such as "find the vacation policy" are sometimes sent to the wrong tool. What is the best fix?

A. Add "Choose the tool carefully" to the system prompt.
B. Add 20 examples where the correct tool is obvious.
C. Remove one of the two tools.
D. Add 2 to 4 examples of ambiguous requests, each explaining why one tool was chosen over the other.

### Q4.2-3 [4.2]
A reviewer keeps flagging an intentional, common short-circuit coding pattern as a bug. The team also wants it to judge similar patterns it has never seen listed. What is the best prompt approach?

A. Include examples that pair acceptable patterns with similar-looking genuine bugs, so the model learns the boundary.
B. List every acceptable pattern in the codebase and tell the model to match only those.
C. Include only examples of real bugs so the model learns what to flag.
D. Tell the model to skip every short-circuit pattern.

### Q4.2-4 [4.2]
A model extracts quantities from recipes. When a recipe says "a handful" or "about 2 cups", it sometimes writes an exact precise number that the recipe never stated. What is the best fix?

A. Mark the quantity field as required so the model always fills it.
B. Add the line "Never hallucinate numbers."
C. Add examples showing how informal measurements like "a handful" and "about 2 cups" should be extracted correctly.
D. Retry each extraction until the number looks precise.

### Q4.2-5 [4.2]
A model extracts citations from research papers. Some papers list citations inline in sentences, and others use a separate bibliography at the end. For inline-citation papers, the extracted citations field often comes back empty even though citations exist. What is the best fix?

A. Mark the citations field as required.
B. Retry each empty result with the message "try again".
C. Add examples showing correct extraction from both inline-citation and bibliography documents.
D. Tell the model to return the whole paper text in the citations field.

---

## Task 4.3

### Q4.3-1 [4.3]
A system asks Claude to reply with JSON in plain text. The parser sometimes fails because of missing brackets or extra commas. Which change is the most reliable way to get well-formed, schema-compliant output?

A. Define an extraction tool whose input schema describes the wanted data, and read the data from the tool call.
B. Add "Respond with valid JSON only" to the prompt.
C. Write a text-cleaning step that fixes common JSON mistakes.
D. Ask the model to answer twice and compare the two replies.

### Q4.3-2 [4.3]
A pipeline receives a mixed pile of documents: invoices, receipts, and purchase orders. There is one extraction tool for each type, and the type of each incoming document is not known in advance. Sometimes the model replies in plain text instead of calling a tool. Which tool_choice setting fixes this?

A. auto
B. A forced call to the invoice extraction tool
C. any
D. none

### Q4.3-3 [4.3]
A document pipeline must always run the extract_metadata tool first on every document. After that, the model should decide freely which enrichment tools to call. Which approach is best?

A. Use auto on the first call and trust the model to start with extract_metadata.
B. Use any on the first call.
C. Write in the prompt "Always call extract_metadata first" and keep auto.
D. Force the named extract_metadata tool on the first call, then use auto for later calls.

### Q4.3-4 [4.3]
An invoice extraction passes schema checks. The three line item amounts add up to $210, but the extracted total field says $250. What does this situation show?

A. Tool use failed, so the team should return to plain-text JSON.
B. Schema enforcement removes syntax errors but does not prevent semantic errors, so separate validation is needed.
C. The total field should be made required in the schema.
D. The model must have been set to auto.

### Q4.3-5 [4.3]
A receipt extraction schema marks customer company as required. Many receipts are personal purchases with no company name, and the model invents company names to fill the field. What is the best fix?

A. Add an "other" value to the company field.
B. Add examples that include invented company names.
C. Force the extraction tool on every call.
D. Make the company field optional and nullable so the model can leave it empty.
