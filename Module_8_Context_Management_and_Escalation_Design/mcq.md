# Module 8 Fast Track: Practice Questions

Pick the single best answer. Answers are in `mcq-answers.md`. Attempt first.

---

## Task statement 5.1

**Q1 [5.1]** A support agent handles a long chat in which the customer raises two separate problems. Problem A is a late order (order A-100, promised by the 14th). Problem B is a billing error (invoice 55, $12 overcharge). The app compacts old turns into a short summary to save space. After compaction, the agent quotes the $12 overcharge in a reply about the late order and no longer knows the promised date. What is the best fix?

A. Switch to a model with a larger context window so compaction is never needed.
B. Keep a separate structured facts block for each issue (IDs, amounts, dates, statuses), sent verbatim every turn and never summarized.
C. Ask the summarizer to produce longer, more detailed summaries.
D. Tell the agent in the system prompt to be careful with amounts and dates.

**Q2 [5.1]** A lead agent combines eight subagent reports into one long input. Each report is similar in length. The final answer regularly misses an important warning that appears in reports 4 and 5, but it includes findings from reports 1 and 8. What is the best change?

A. Add the instruction "read every report carefully" at the top.
B. Split the reports across eight separate API calls and concatenate the answers.
C. Ask each subagent to write longer reports so warnings stand out.
D. Put a short key-findings summary at the start of the input and organize the detailed reports under explicit section headers.

**Q3 [5.1]** An order-lookup tool returns 40 fields per call. For return requests, only four fields matter: order ID, status, amount, and return-eligible. After several lookups, the agent's context is nearly full and responses get worse. What is the best fix?

A. Trim each tool result to the four relevant fields before it is added to the conversation.
B. Remove the order-lookup tool and ask the customer for the details.
C. Summarize the whole conversation after every turn.
D. Keep all 40 fields so no information is ever lost.

**Q4 [5.1]** A developer builds a quote assistant on the Messages API. To save tokens, each request sends only the customer's newest message. The customer already gave car make, model, and year. The assistant keeps asking for the year again. What is the cause and best fix?

A. The model has a bug; wait for the provider to fix it.
B. Add "remember earlier answers" to the system prompt.
C. The API keeps no memory between requests; the app must send the full message history (or a faithful summary) each time.
D. Use a higher temperature so the model recalls earlier turns.

**Q5 [5.1]** A research subagent produces an 8,000-token transcript of its reasoning plus findings. The downstream report-writer agent has a small context budget. It also gets two similar statistics from two subagents and cannot tell which is newer or where each came from. What is the best redesign?

A. Have the subagent return a compact structured payload (key facts, citations, relevance scores) that includes dates, source locations, and method for each finding.
B. Pass the full transcript and ask the writer agent to find what matters.
C. Have the subagent return one paragraph of prose with no sources, to keep it short.
D. Have the writer agent re-run the research itself.

---

## Task statement 5.2

**Q1 [5.2]** A store's written policy allows price-matching against the store's own earlier sale prices. It says nothing about competitor prices. A customer politely asks the support agent to match a competitor's lower price. What should the agent do?

A. Approve the match, because the policy does not forbid it.
B. Deny the request, because the policy only mentions the store's own prices.
C. Escalate to a human, because the policy is silent on this request.
D. Approve it only if the customer sounds upset.

**Q2 [5.2]** A customer writes: "Get me a human agent now." The issue is a simple address change the agent could handle in one step. What should the agent do?

A. Escalate immediately, without first trying to resolve the issue.
B. Complete the address change first, then offer a human if the customer is still unhappy.
C. Ask the customer to explain the problem so the agent can judge whether a human is needed.
D. Check the model's confidence score, and escalate only if it is low.

**Q3 [5.2]** A customer writes: "This is so annoying, my order is three days late!" They do not ask for a human. Checking order status is something the agent can do. What is the best behavior?

A. Escalate immediately, because the customer is frustrated.
B. Ignore the tone and reply only with the tracking number.
C. Tell the customer the agent cannot help with late orders.
D. Acknowledge the frustration, offer to check and resolve the order, and escalate only if the customer repeats that they want a human.

**Q4 [5.2]** A team wants fewer wrong escalations in its support agent. Today it escalates when a sentiment score is negative or when the model reports low confidence. Calm, polite customers with policy exceptions are not escalated, and angry customers with easy questions are. What is the best change?

A. Lower the sentiment threshold so more messages escalate.
B. Put explicit escalation criteria in the system prompt (human requested, policy gap, no progress possible) with few-shot examples of escalate versus resolve decisions.
C. Ask the model to rate its own confidence more carefully.
D. Escalate every case that needs more than three tool calls.

**Q5 [5.2]** An agent searches for a customer by name. The tool returns two accounts, both named "Maria Lopez". The customer wants a refund on the account. What should the agent do?

A. Pick the account with the most recent activity, because it is most likely correct.
B. Pick the first result in the list.
C. Ask the customer for another identifier, such as an email or order number, before acting.
D. Apply the refund to both accounts to be safe.
