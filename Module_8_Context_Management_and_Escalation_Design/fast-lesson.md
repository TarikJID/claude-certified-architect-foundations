# Module 8 Fast Track: Context and Escalation

## 5.1 Keep key facts alive in long conversations

**Setting:** A support agent built on Claude chats with customers and uses tools (actions it can call, such as "look up order"). In long chats it mixes up amounts and dates, and its memory fills with unneeded data.

**Before/after:** Before: old messages are shortened to "customer wants a quick fix, discussed price". After: a fixed note goes with every message: "order A-88213, refund $47.50, promised by 19 Sept".

**Exam rule:** Protect exact facts, keep memory small, put important things first.

- Summaries blur numbers and dates. Pick: a "case facts" block (that fixed note), sent unchanged every turn, never summarized. Two problems: one block each. Trap: "use a bigger context window" (how much text the model sees at once). Fails: accuracy drops as text grows.
- An order lookup returns 40 pieces of data; 5 matter. Pick: keep only those 5.
- Claude keeps no memory between messages. Pick: the app resends the full chat each time.
- Own setting: a main agent combines reports from several helper agents. Models miss the middle of long text. Pick: key-findings summary first, clear headings below.
- Same setting: helpers return short structured results (facts, sources, relevance) with dates and method. Trap: sending their full reasoning. Fails: it overflows the next agent's limited space.

## 5.2 Decide when to hand a chat to a human

**Setting:** The same support agent can look up customers, refund, or escalate (hand the chat to a human). It escalates easy cases and misses real policy problems.

**Before/after:** Before: "escalate if the customer seems upset or the case looks hard". After: "escalate if they ask for a person, the policy does not cover it, or you cannot make progress", with examples.

**Exam rule:** Escalate on those three triggers only. A five-step refund that fits the policy stays with the agent.

- "I want a person": escalate at once. Investigating first ignores the request.
- Annoyed ("my order is three days late"), no request for a person, simple fix: acknowledge, offer to fix. Escalate only if they ask again.
- Policy covers the store's own past prices, says nothing about competitors. Competitor price match: escalate. Guessing can make a wrong promise.
- Name search finds two "John Smith" accounts: ask for email or order number. Trap: picking the newest. Fails: it can refund the wrong person.
- Trap: escalating on a sentiment score (rating of how upset a message sounds) or the model's own confidence. Fails: angry customers can have easy problems; the model can be confidently wrong. Fix: the three triggers in the system prompt (standing instructions) with few-shot examples (short worked examples).
