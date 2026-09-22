# Module 5 Quizzes

Answers are in `quiz-answers.md`, deliberately not in this file.

Attempt each question before opening it.

---

## Quiz — Lesson 3.4 (Plan Mode vs Direct Execution)

**Q1.** A developer needs to migrate a widely-used HTTP client library across 45+
files. Should they use plan mode or direct execution? Why?

**Q2.** Why is plan mode considered "safe" for exploration, mechanically?

**Q3.** What is the Explore subagent, and why is it used during multi-phase
discovery tasks instead of having the main agent do the searching itself?

**Q4.** Describe a workflow that combines plan mode and direct execution in a
single task, and explain why you wouldn't just use plan mode for everything.

---

## Quiz — Lesson 3.5 (Iterative Refinement)

**Q1.** A prose instruction "validate email addresses" produces inconsistent
results. What's the most effective fix, and give an example.

**Q2.** Describe test-driven iteration as an iterative-refinement technique. What
makes the loop "close on its own"?

**Q3.** What is the interview pattern, and when is it most useful?

**Q4.** Two bugs both touch the same discount-calculation function. A third,
unrelated bug is a typo in a footer. How should these be reported/fixed, and why?

---

## Quiz — Lesson 3.6 (CI/CD Integration)

**Q1.** Why does an interactive `claude` session hang in a CI pipeline, and what
flag fixes it?

**Q2.** How do you get machine-parseable, schema-conformant output from a
`claude -p` invocation in CI, and where does the result appear?

**Q3.** Why should a CI code-review step use a freshly-started Claude session
rather than the same session that generated the code?

**Q4.** A review pipeline re-runs after every new commit and keeps re-posting the
same PR comment for an issue that's already been fixed. What's the fix, and what
mechanism makes CLAUDE.md relevant even in a non-interactive CI run?
