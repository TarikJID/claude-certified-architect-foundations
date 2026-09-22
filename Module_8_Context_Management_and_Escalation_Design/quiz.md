# Module 8 Quizzes

Answers are in `quiz-answers.md`, deliberately not in this file.

Attempt each question before opening it.

---

## Quiz — Lesson 5.1 (Managing Conversation Context)

**Q1.** A 10-report synthesis puts a critical caveat in report #5 of 10. Why is
that caveat statistically more likely to be dropped than one in report #1 or #10?

**Q2.** A customer said "I need this resolved by Friday the 14th, and I was
quoted $47.50." After compaction, the summary reads "Customer requested timely
resolution and discussed pricing." What went wrong, and what's the fix?

**Q3.** An order-lookup tool returns 40 fields but only 5 are relevant to a
return request. What should happen to the other 35, and why does the Messages
API's statelessness make this the application's responsibility rather than the
API's?

**Q4.** How should a synthesis prompt aggregating several subagents' reports be
structured to counter position effects?

**Q5.** A downstream synthesis agent has a small context budget. Should an
upstream research subagent hand it its full 8,000-token exploration transcript
including reasoning chains, or something else? Why?

---

## Quiz — Lesson 5.2 (Escalation and Ambiguity Resolution)

**Q1.** A refund request takes five tool calls but resolves cleanly under
existing policy. Should the agent escalate just because it was complex? Why or
why not?

**Q2.** A customer explicitly says "I want to talk to a person." What should the
agent do, and what should it NOT do first?

**Q3.** Why are sentiment analysis and the model's own self-reported confidence
score both unreliable as the primary basis for an escalation decision?

**Q4.** A customer lookup by name returns two matching accounts. What should the
agent do, and what should it avoid doing?

**Q5.** A store's policy covers price-matching its own past sales but says
nothing about matching a competitor's price. A customer asks for a competitor
price match. What should the agent do, and why is "the policy doesn't forbid it,
so I'll approve it" the wrong reasoning?
