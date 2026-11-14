# Module 9 MCQ answers (fast track)

Tutor: reveal only after the learner has attempted the question.

Answer key: 5.3 Q1 B, Q2 D, Q3 A, Q4 C, Q5 B. 5.4 Q1 C, Q2 A, Q3 D, Q4 B, Q5 C.

---

## Task statement 5.3

**Q1 — Correct: B.** Tests 5.3-K1, 5.3-S1, 5.3-K3.
Why: Failure type, attempt, partial results and alternatives let the coordinator choose a recovery.
- A wrong: a generic status hides exactly the context the coordinator needs.
- C wrong: partial results presented as complete misleads the coordinator.
- D wrong: an empty result returned as success is silent suppression of a real failure.

**Q2 — Correct: D.** Tests 5.3-K2, 5.3-S2.
Why: A timeout may be worth retrying; a completed query with zero matches is a trustworthy answer.
- A wrong: merging them removes the information needed to decide on a retry.
- B wrong: a valid empty result is not an error, and labelling it one wastes retries.
- C wrong: it is reversed; it hides the failure and flags the valid result.

**Q3 — Correct: A.** Tests 5.3-K4, 5.3-S4.
Why: Targeted recovery keeps the three finished results and discloses the gap.
- B wrong: stopping everything over one failure wastes completed work.
- C wrong: "no data found" suppresses the error and presents incomplete work as complete.
- D wrong: it throws away successful work and may loop on a source that is down.

**Q4 — Correct: C.** Tests 5.3-S3, 5.3-K3, 5.3-S1.
Why: The subagent recovers locally first, and only escalates with what it tried and partial results.
- A wrong: it escalates too early with a generic message.
- B wrong: it hides the failure as a successful empty result.
- D wrong: subagents should handle transient failures themselves before propagating.

**Q5 — Correct: B.** Tests 5.3-S4, 5.3-K4.
Why: Coverage annotations separate well-supported findings from gaps caused by unavailable sources.
- A wrong: silent omission looks like full coverage.
- C wrong: unlabelled filler presents unsupported content as established.
- D wrong: a partial, honestly labelled report is better than none.

---

## Task statement 5.4

**Q1 — Correct: C.** Tests 5.4-K1, 5.4-K2, 5.4-S2.
Why: Generic "typical patterns" answers are the sign of context degradation. A scratchpad file or fresh session counters it.
- A wrong: the model did read the class; the earlier finding was lost, not missing.
- B wrong: nothing indicates the tool results were wrong, and rerunning adds more bloat.
- D wrong: the symptom concerns the model's recall, not a code defect.

**Q2 — Correct: A.** Tests 5.4-K3, 5.4-S1.
Why: A subagent explores in its own context and returns only a summary, so the main context stays clean.
- B wrong: all raw search output would accumulate in the main context.
- C wrong: reading every file upfront is the worst case for context bloat.
- D wrong: it pushes the work onto the user and does not use subagents.

**Q3 — Correct: D.** Tests 5.4-S5.
Why: `/compact` summarizes the history and can be steered; using it before context is full gives more control than waiting.
- A wrong: automatic compaction gives less control over what survives.
- B wrong: it discards the refund-flow findings that are still needed.
- C wrong: CLAUDE.md is project configuration, not the verbose discovery output causing the problem.

**Q4 — Correct: B.** Tests 5.4-K4, 5.4-S4.
Why: State exports plus a manifest let the coordinator reload finished work and inject it into prompts.
- A wrong: state held only in context is lost in a crash or truncation.
- C wrong: it repeats completed work, which is the thing to avoid.
- D wrong: compaction shrinks context in a live session; it is not crash recovery.

**Q5 — Correct: C.** Tests 5.4-S3.
Why: A summary gives the next phase relevant context without the bloated history.
- A wrong: the full transcript bloats each subagent's context.
- B wrong: the next phase would have to rediscover what phase 1 found.
- D wrong: subagents start with a fresh context and do not inherit parent history.
