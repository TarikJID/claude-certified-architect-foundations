# Module 2 Quizzes

Answers are in `quiz-answers.md`, deliberately not in this file.

Attempt each question before opening it.

---

## Quiz — Lesson 1.4 (Workflows, Enforcement, Handoff)

**Q1.** Why do prompt instructions alone have a non-zero failure rate for
enforcing order-of-operations, and what is the deterministic alternative?

**Q2.** How does a `PreToolUse`-based prerequisite gate guarantee that
`process_refund` can never run before `get_customer` has verified the customer —
even in a permissive permission mode?

**Q3.** A customer message says "my order arrived damaged AND I was charged
twice." What decomposition approach should the agent use, and how should the
final response be structured?

**Q4.** What four elements should a structured handoff summary to a human agent
include, and why does it matter that a human receiving the handoff typically
lacks conversation transcript access?

---

## Quiz — Lesson 1.5 (Hooks: Interception and Normalization)

**Q1.** What is the difference between a `PostToolUse` hook and a `PreToolUse`
hook in terms of when they run and what they're typically used for?

**Q2.** Two MCP tools — `orders` and `billing` — represent order status
differently: one as an integer code, one as a string enum. What mechanism fixes
this before Claude reasons over both, and why does this discrepancy exist in the
first place?

**Q3.** A `PreToolUse` hook denies a `process_refund` call for exceeding $500. What
should the hook's denial *also* do, beyond simply blocking the call, and why?

**Q4.** What does the MCP `isError` flag let an agent do that a protocol-level
JSON-RPC error would not?

---

## Quiz — Lesson 1.6 (Task Decomposition Strategies)

**Q1.** You're designing a workflow to review 20 pull requests every week, each
checked against the same 5 fixed criteria. Should you use prompt chaining or
dynamic adaptive decomposition? Why?

**Q2.** Why does reviewing a 40-file pull request as one single LLM call risk
worse quality than splitting it into per-file passes plus a cross-file pass?

**Q3.** For "add comprehensive tests to a legacy codebase" — an open-ended task —
describe the staged, adaptive decomposition strategy from this lesson.

**Q4.** What is the key difference between prompt chaining and dynamic adaptive
decomposition?

---

## Quiz — Lesson 1.7 (Session State, Resumption, Forking)

**Q1.** A developer wants to return to a specific named investigation among
several sessions run in the same directory. Which command do they use, and how
does it differ from simply "continuing"?

**Q2.** A developer has fully analyzed a codebase's authentication module in one
session and now wants to explore two different refactoring approaches (JWT vs
OAuth2) without either exploration contaminating the other or redoing the shared
analysis. What feature should they use?

**Q3.** A session previously analyzed `payment.py`, which has since been modified
by a teammate. What should the developer do when resuming the session, and why?

**Q4.** When is starting a fresh session with an injected structured summary more
reliable than resuming a prior session?
