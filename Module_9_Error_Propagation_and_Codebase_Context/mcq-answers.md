# Module 9 MCQ answers (fast track)

Tutor: reveal only after the learner has attempted the question.

Answer key: 5.3 Q1 B, Q2 D, Q3 A, Q4 C, Q5 B. 5.4 Q1 C, Q2 A, Q3 D, Q4 B, Q5 C.

---

## Task statement 5.3

**Q1 — Correct: B.** Tests 5.3-K1, 5.3-S1, 5.3-K3.
Why: Saying what failed, what was tried, what was found and what else could work lets the coordinator pick the next step.
- A wrong: "search failed" gives the coordinator nothing to decide with.
- C wrong: calling 2 of 5 articles the full result misleads the coordinator.
- D wrong: an empty list marked "success" hides a real failure.

**Q2 — Correct: D.** Tests 5.3-K2, 5.3-S2.
Why: The timeout might work on a retry; a search that worked and found nothing will give the same answer again.
- A wrong: lumping them together removes what the coordinator needs to decide on a retry.
- B wrong: a search that worked is not an error, and calling it one wastes retries.
- C wrong: it is the wrong way round; it hides the failure and flags the good result.

**Q3 — Correct: A.** Tests 5.3-K4, 5.3-S4.
Why: The user gets a report today, the three good findings are kept, and the gap is stated.
- B wrong: stopping everything over one failure throws away finished work and gives no report.
- C wrong: "no data found" pretends the search worked, so the report looks complete when it is not.
- D wrong: it wastes the good results and may keep failing while the source is down.

**Q4 — Correct: C.** Tests 5.3-S3, 5.3-K3, 5.3-S1.
Why: The subagent fixes short glitches itself and only reports up, with what it tried, when it cannot.
- A wrong: it reports too early, and with a vague message.
- B wrong: it hides the failure as a successful empty search.
- D wrong: subagents should handle short glitches themselves before reporting up.

**Q5 — Correct: B.** Tests 5.3-S4, 5.3-K4.
Why: Coverage notes tell readers which parts are well supported and which have gaps.
- A wrong: silently leaving a topic out makes the report look complete.
- C wrong: unlabelled filler looks as reliable as the sourced findings, which it is not.
- D wrong: an honest partial report is better than none.

---

## Task statement 5.4

**Q1 — Correct: C.** Tests 5.4-K1, 5.4-K2, 5.4-S2.
Why: "Typically" answers about code it already read are the sign of a long session losing track. A notes file or a fresh session fixes it.
- A wrong: the agent did read the code; the finding faded, it was never missing.
- B wrong: nothing says the searches were wrong, and rerunning adds more clutter.
- D wrong: the problem is the agent's memory, not a fault in the code.

**Q2 — Correct: A.** Tests 5.4-K3, 5.4-S1.
Why: The subagent does the long search in its own memory and hands back only a summary, so the main agent stays clear.
- B wrong: all the raw search output would pile up in the main agent's context.
- C wrong: opening every file first fills the context the fastest.
- D wrong: it pushes the work onto the engineer and does not use a subagent.

**Q3 — Correct: D.** Tests 5.4-S5.
Why: Running `/compact` early with an instruction frees space and keeps the refund findings on purpose.
- A wrong: automatic compaction waits until nearly full and takes no instructions, so you control less of what survives.
- B wrong: it throws away the refund findings that are still needed.
- C wrong: CLAUDE.md holds team instructions; it is not what is filling the context.

**Q4 — Correct: B.** Tests 5.4-K4, 5.4-S4.
Why: Saved progress files plus a manifest let the lead agent reload finished work instead of redoing it.
- A wrong: progress held only in working memory is lost in the crash.
- C wrong: it reruns finished subagents, which the constraint forbids.
- D wrong: compaction shrinks a running conversation; it does not survive a crash.

**Q5 — Correct: C.** Tests 5.4-S3.
Why: A summary gives phase 2 what phase 1 learned without the long record.
- A wrong: the full record floods each subagent.
- B wrong: phase 2 would have to rediscover what phase 1 already found.
- D wrong: new subagents start blank and do not see earlier work unless given it.
