# Module 6 Fast Lesson

## 4.1 Explicit criteria to cut false positives

Exam rule: Tell the model exactly which issues to report and which to skip. Vague or confidence-based wording does not raise precision.

- Pick: category rules (report bugs and security; skip minor style and local patterns).
- Pick: a checkable test, not a feeling.
- Pick: each severity level paired with a concrete code example.
- Pick: temporarily disable a category with a high false positive rate, fix its prompt, then re-enable it. One noisy category makes developers distrust the accurate ones too.
- Reject: "be conservative" and "only report high-confidence findings". Trap: they sound safe, but the model's confidence is not calibrated to your tolerance.

Example: "Flag a comment only when it contradicts what the code does" beats "check that comments are accurate".

## 4.2 Few-shot examples for consistency

Exam rule: When detailed instructions still give inconsistent output, add a few worked examples. Examples show the result; prose only describes it.

- Pick: 2-4 examples aimed at the ambiguous cases, each with the reason one action beat the alternatives.
- Pick: examples that show the full output format (location, issue, severity, suggested fix).
- Pick: examples that pair an acceptable pattern with a similar real issue. This cuts false positives and lets the model judge new patterns.
- Pick: examples of varied document layouts and informal measurements. This cuts invented values and empty fields.
- Reject: longer prose, "do not hallucinate" lines, and confidence thresholds. Trap: more instructions rarely fix inconsistency.

Example: An example showing "~2 cups" handled correctly stops the model inventing exact amounts.

## 4.3 Structured output with tool use and JSON schemas

Exam rule: Define a tool with a JSON schema and read the tool call for guaranteed-format output. A schema fixes syntax, not correctness.

- tool_choice: auto may return text. any must call some tool; use it when the document type is unknown. A forced named tool must be called; use it to run one step first.
- Schema valid is not the same as right. Line items that miss the total are a semantic error and need validation.
- Use optional, nullable fields when data may be missing. Required fields push the model to invent values.
- Use enums with "other" plus a detail field, and "unclear" for ambiguous cases.
- Put normalization rules in the prompt (for example one date format) alongside the schema. Trap: "the schema makes the data consistent and correct".
