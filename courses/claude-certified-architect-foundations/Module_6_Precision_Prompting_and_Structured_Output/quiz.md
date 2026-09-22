# Module 6 Quizzes

Answers are in `quiz-answers.md`, deliberately not in this file.

Attempt each question before opening it.

---

## Quiz — Lesson 4.1 (Explicit Criteria and False Positives)

**Q1.** Contrast "check that comments are accurate" with "flag comments only when
claimed behavior contradicts actual code behavior." Which is more effective and
why?

**Q2.** Why doesn't telling a review prompt to "only report high-confidence
findings" reliably reduce false positives?

**Q3.** A "minor style" finding category is wrong 40% of the time. Why might this
hurt trust in the "security" category too, and what's the recommended
mitigation?

**Q4.** Why pair severity level names (critical/high/medium/low) with concrete
code examples?

---

## Quiz — Lesson 4.2 (Few-Shot Prompting)

**Q1.** A prompt describes the desired output format in detailed prose but output
is still inconsistently formatted. What technique should you apply, and why is it
more effective than more prose?

**Q2.** For a tool-selection task where a request could plausibly map to either
of two tools, what should a good few-shot example include beyond just the
correct answer?

**Q3.** Why does showing both an acceptable pattern example and a genuinely buggy
(but superficially similar) pattern example help the model generalize to novel,
unseen inputs?

**Q4.** How do few-shot examples reduce hallucination specifically in extraction
tasks, and give an example of the kind of hard case they address.

---

## Quiz — Lesson 4.3 (Structured Output via Tool Use and JSON Schema)

**Q1.** Why does defining an extraction tool with a JSON Schema `input_schema`
and having Claude call it produce more reliable structured output than asking
Claude to "return the data as JSON" in prose?

**Q2.** An invoice extraction is schema-valid: every field has the right type,
`total` is present. But the three `line_items` amounts sum to $210 while `total`
reads $250. Did tool-use-enforced structured output fail here? Explain.

**Q3.** A `document_type` field needs to handle document types not anticipated at
design time. How should the schema be designed?

**Q4.** Multiple extraction tools exist (`extract_invoice`, `extract_receipt`,
`extract_purchase_order`) and you don't know the incoming document's type ahead
of time. Which `tool_choice` setting guarantees a structured call while still
letting the model pick the right schema?

**Q5.** A `customer.company` field is marked `required`, but many source
documents (personal purchases) have no company name. What happens, and how
should the schema be fixed?
