# Module 1 Quizzes

Answers are in `quiz-answers.md`, deliberately not in this file.

Attempt each question before opening it.

---

## Quiz — Lesson 1.1 (Agentic Loops)

**Q1.** What field on the model's response drives the agentic loop's
continue/terminate decision, and what are its two relevant values?

**Q2.** Why must a tool's result be explicitly appended to conversation history
rather than simply having happened?

**Q3.** Name the three agentic loop termination anti-patterns described in this
lesson, and explain why each is unreliable.

**Q4.** How does model-driven decision-making in an agentic loop differ from a
pre-configured decision tree?

---

## Quiz — Lesson 1.2 (Coordinator-Subagent Orchestration)

**Q1.** In a hub-and-spoke multi-agent architecture, can subagents communicate
directly with each other? What passes through the coordinator?

**Q2.** A subagent just finished reading 40 documents. Does the coordinator's
context now contain those 40 documents? Why or why not?

**Q3.** A coordinator splits "research the semiconductor shortage" across three
subagents with no further guidance. What is the likely failure mode, and what
should the coordinator have done instead?

**Q4.** After a first synthesis pass, the coordinator notices a topic gap. What
should it do?

---

## Quiz — Lesson 1.3 (Subagent Invocation, Context Passing, Spawning)

**Q1.** A coordinator has `agents={"reviewer": AgentDefinition(...)}` configured
but `allowed_tools=["Read", "Grep"]`. Will the coordinator be able to invoke the
`reviewer` subagent? Why or why not?

**Q2.** A coordinator invokes a synthesis subagent with the prompt "use the
findings from the earlier search." Why is this likely to fail?

**Q3.** What two fields are minimally required in an `AgentDefinition`, and what
does each control?

**Q4.** A coordinator wants to spawn three subagents to research three separate
frameworks at the same time. What must it do in a single response to achieve true
parallelism, and what session-management feature would instead let two already-
completed analyses diverge into separate follow-up investigations from the same
baseline?

**Q5.** Why are goal-oriented coordinator prompts generally preferred over
step-by-step procedural instructions for subagents — and what four elements
should a goal-oriented prompt still include?
