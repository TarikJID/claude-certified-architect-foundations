# Module 8 — Quiz answers

> Held separately from `quiz.md` on purpose: so a tutor asking a question does
> not have the answer sitting in its context. Attempt first.

## Quiz — Lesson 5.1 (Managing Conversation Context)

**Q1.** The "lost in the middle" effect: models are most reliable at using information
near the beginning and end of a long input, and least reliable at using
information buried in the middle, because self-attention's capacity to relate any
token to the rest of the input is finite and dilutes as context grows.

**Q2.** Progressive summarization risk: a summarizer optimizing for brevity
preferentially condenses precise, low-frequency tokens (exact dates, dollar
amounts) into vague paraphrases. Fix: extract such transactional facts into a
persistent "case facts" block included verbatim in every prompt, outside the
summarized/compacted history.

**Q3.** The other 35 fields should be trimmed/cleared before or after insertion into
context (tool-result clearing) since they consume tokens disproportionate to
their relevance. Because the Messages API is stateless and simply echoes back
whatever's in the request each time, any trimming, summarizing, or restructuring
of history must happen client-side — the API does not do it implicitly.

**Q4.** Place a short summary of key findings at the very beginning, organize detailed
supporting material underneath with explicit section headers, and place the
actual query/analysis instruction after the long content rather than before it.

**Q5.** Something else — a compact, structured payload (key facts, citations, relevance
scores) rather than verbose prose and reasoning chains. This mirrors the
sub-agent pattern of returning only a condensed, distilled summary of work, so
the downstream agent gets the decision-relevant content without exceeding its
context budget.


## Quiz — Lesson 5.2 (Escalation and Ambiguity Resolution)

**Q1.** No. Complexity alone, in the absence of an explicit human request, a policy
exception/gap, or an inability to make progress, is not by itself a sufficient
escalation trigger under the escalation trigger taxonomy.

**Q2.** Honor the request immediately and escalate without first attempting its own
investigation or resolution. Investigating first would read as the agent
overriding the customer's stated preference.

**Q3.** Sentiment: a customer can be highly frustrated about a trivially resolvable
issue and calm about a genuinely complex one, so tone doesn't track actual
complexity. Self-reported confidence: a model can be confidently wrong or
under-confident on a case it's actually handling correctly, so its own estimate
isn't a reliable proxy either.

**Q4.** Ask the customer for an additional identifier (order number, email, ZIP code) to
disambiguate. It should avoid picking one match using a heuristic (e.g. most
recent), because that risks silently acting on the wrong customer's data.

**Q5.** Escalate. This falls under "policy silence/ambiguity" — when written policy
simply doesn't address a request, silence is not permission, and an incorrect
improvised answer can create liability or an inconsistent precedent. The agent
should not infer approval from adjacent-but-not-identical policy language.
