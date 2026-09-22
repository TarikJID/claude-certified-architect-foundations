# Module 6 — Quiz answers

> Held separately from `quiz.md` on purpose: so a tutor asking a question does
> not have the answer sitting in its context. Attempt first.

## Quiz — Lesson 4.1 (Explicit Criteria and False Positives)

**Q1.** The second is more effective — it's an explicit, checkable criterion, while the
first is vague and leaves "accurate" undefined. Explicit criteria give the model
(and a human auditor) a concrete test to apply, rather than an open-ended
standard it must infer.

**Q2.** It asks the model to self-estimate a confidence threshold rather than apply a
defined rule, and the model's internal notion of "high confidence" isn't
calibrated to the reviewer's actual tolerance. Specific categorical criteria
(which categories to report vs. skip) outperform confidence-based filtering.

**Q3.** A high false-positive rate in one category erodes trust in the whole system —
once a reviewer learns to distrust and skim past one noisy category, they tend to
under-scrutinize adjacent, accurate categories too. Mitigation: temporarily
disable the high-false-positive category to restore trust in the rest, while its
prompt is iterated on.

**Q4.** Defining severity purely by name invites inconsistent classification because
terms like "critical" mean different things across reviewers and runs. A
concrete example anchors each level to a specific reference point, producing
more consistent classification.


## Quiz — Lesson 4.2 (Few-Shot Prompting)

**Q1.** Few-shot prompting — add a small set of worked examples. Examples show, rather
than describe, the exact shape and quality bar output must meet, which is harder
for a model to under- or over-generalize from than a prose rule.

**Q2.** The reasoning for why the chosen action was preferred over the other plausible
alternative — not just the final input/output pair — so the model learns the
discriminating signal, not just a lookup-table case.

**Q3.** It teaches the model the underlying judgment / distinguishing feature between the
two, rather than a lookup table of specific cases — this lets it correctly judge
a third, unseen pattern by applying the same distinguishing logic.

**Q4.** They show concrete instances of correct handling for hard cases that otherwise
invite fabrication — e.g., informal measurements like "~2 cups" correctly
normalized, or a citation embedded mid-sentence correctly attributed — preventing
the model from fabricating a precise value or returning an empty field for a
format it hasn't seen described in prose.


## Quiz — Lesson 4.3 (Structured Output via Tool Use and JSON Schema)

**Q1.** The model's tool call must conform to the declared parameter shape, which
eliminates the class of errors from asking the model to emit raw JSON as free
text (missing quotes, trailing commas, truncated braces) — the structured data is
read directly from the `tool_use` block's `input`.

**Q2.** No schema violation occurred — this is a semantic error, not a syntax error.
Strict JSON schemas via tool use eliminate syntax errors but cannot by themselves
prevent values that are individually well-formed but collectively wrong.

**Q3.** Use an enum with an escape-hatch `"other"` value paired with a free-text `detail`
field (e.g. `document_type_detail`), plus an explicit `"unclear"` value for
genuinely ambiguous cases — giving the model a truthful option instead of forcing
a best-guess match to an existing enum value.

**Q4.** `tool_choice: {"type": "any"}` — it forces Claude to call one of the available
tools rather than returning conversational text, while still letting the model
choose which tool (schema) best fits the document.

**Q5.** The model is forced to either fail or fabricate a company name to satisfy the
required constraint. Fix: mark the field optional and nullable (not in
`required`, typed to accept `null`), so the model can correctly return `null`
when the information legitimately isn't present.
