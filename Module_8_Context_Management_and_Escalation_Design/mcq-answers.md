# Module 8 Fast Track: Answers

Tutor only: do not reveal before the learner has attempted the question.

---

## Task statement 5.1

**Q1 [5.1]** Correct: B. Tests: 5.1-K1, 5.1-S1, 5.1-S2.
- Why: Exact amounts and dates are what summaries blur; a verbatim facts block per issue is outside summarization and keeps issues apart.
- A wrong: A bigger window delays the problem and does not stop summaries blurring details.
- C wrong: Longer summaries still paraphrase exact values and do not keep issues separate.
- D wrong: A prompt reminder cannot restore details already removed from context.

**Q2 [5.1]** Correct: D. Tests: 5.1-K2, 5.1-S4.
- Why: Models handle the start and end of long inputs best and miss the middle; a key-findings summary up front plus headers counters this.
- A wrong: An instruction does not change the position effect.
- B wrong: Separate calls lose the cross-report synthesis and are not the recommended fix.
- C wrong: Longer reports make the input longer and the middle bigger.

**Q3 [5.1]** Correct: A. Tests: 5.1-K3, 5.1-S3.
- Why: Trimming to relevant fields before insertion stops irrelevant tokens piling up.
- B wrong: Removing the tool loses a needed capability.
- C wrong: Whole-conversation summaries risk losing exact facts and do not target the bloat.
- D wrong: Keeping everything is what causes the bloat.

**Q4 [5.1]** Correct: C. Tests: 5.1-K4.
- Why: The Messages API is stateless, so the app must resend the history it wants Claude to see.
- A wrong: This is expected API behavior, not a bug.
- B wrong: A prompt cannot give the model turns that were never sent.
- D wrong: Temperature does not add memory.

**Q5 [5.1]** Correct: A. Tests: 5.1-S5, 5.1-S6.
- Why: A compact structured payload fits the small budget, and metadata (dates, sources, method) lets the writer tell the two statistics apart.
- B wrong: The full transcript overwhelms the small budget.
- C wrong: Unsourced prose removes the metadata the writer needs.
- D wrong: Re-running the research wastes the subagent's work and fills the writer's context.

---

## Task statement 5.2

**Q1 [5.2]** Correct: C. Tests: 5.2-K1, 5.2-S4.
- Why: A policy gap or silence is an escalation trigger; silence is not permission.
- A wrong: Approving by inference can create liability or precedent.
- B wrong: Denying by inference is the same improvising in the other direction.
- D wrong: Mood is not an escalation criterion.

**Q2 [5.2]** Correct: A. Tests: 5.2-K2, 5.2-S2.
- Why: An explicit request for a human is honored immediately, with no investigation first.
- B wrong: Resolving first overrides the customer's stated preference.
- C wrong: Asking for an explanation first delays the explicit request.
- D wrong: Self-reported confidence is unreliable and irrelevant to an explicit request.

**Q3 [5.2]** Correct: D. Tests: 5.2-K2, 5.2-S3.
- Why: With no human request and a simple issue, acknowledge, offer a fix, and escalate only if the customer repeats the request.
- A wrong: Frustration alone is not an escalation trigger.
- B wrong: Ignoring the frustration is poor service.
- C wrong: The agent can check order status, so refusing is wrong.

**Q4 [5.2]** Correct: B. Tests: 5.2-K3, 5.2-S1, 5.2-K1.
- Why: Sentiment and self-reported confidence are unreliable proxies; explicit triggers plus few-shot examples steer behavior consistently.
- A wrong: More sentiment-based escalation worsens the same flaw.
- C wrong: Self-rated confidence is still an unreliable proxy.
- D wrong: Complexity alone is not a trigger; a clean five-call case should not escalate.

**Q5 [5.2]** Correct: C. Tests: 5.2-K4, 5.2-S5.
- Why: Multiple matches need an extra identifier, not a guess.
- A wrong: Recency is a heuristic that can act on the wrong customer.
- B wrong: List order is also a heuristic.
- D wrong: Refunding both accounts causes a real error.
