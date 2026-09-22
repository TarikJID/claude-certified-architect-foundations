# Module 9 Quizzes

Answers are in `quiz-answers.md`, deliberately not in this file.

Attempt each question before opening it.

---

## Quiz — Lesson 5.3 (Error Propagation Across Multi-Agent Systems)

**Q1.** A subagent's search times out. Instead of reporting "search failed,"
what should it report, and why does that help the coordinator?

**Q2.** Why must "access failure" and "valid empty result" be reported
differently by a subagent, even though both might look like "nothing came back"?

**Q3.** A market-data subagent fails while three others succeed. Name the two
anti-patterns a coordinator might fall into, and describe the better response.

**Q4.** Should a subagent report every transient failure straight to the
coordinator? What should it do first, and what must it include if it does end up
escalating?

**Q5.** Why is "search unavailable" a worse error message than "Rate limit
exceeded on internal search API; retry after 60s, or use the cached index as a
fallback"?

---

## Quiz — Lesson 5.4 (Context in Large Codebase Exploration)

**Q1.** Forty tool calls into an exploration session, the model answers a
question about a specific class with a generic statement about how such classes
"typically" behave, rather than citing what it actually found earlier. What is
this a symptom of, and what's the standard mitigation?

**Q2.** What's the purpose of a scratchpad/progress file during a multi-session
refactor, and why does it survive problems that in-context memory doesn't?

**Q3.** Instead of having the main agent grep through hundreds of files itself,
what should it do, and what specifically stays out of the main agent's context as
a result?

**Q4.** Why does Anthropic's research-agent system save its plan to persistent
memory (a structured state export) rather than keeping it only in the agent's own
context?

**Q5.** What does `/compact` do, and why is running it proactively (before
context is nearly exhausted) better than waiting for automatic compaction?
