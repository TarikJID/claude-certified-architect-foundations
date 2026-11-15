# Module 8 Fast Track: Practice Questions

Pick the single best answer. Answers are in `mcq-answers.md`. Attempt first.

---

## Task statement 5.1

**Q1 [5.1]** A company's customer support agent, built on Claude, is in a long chat about two separate problems. Problem A is a late order: order A-100, promised by the 14th. Problem B is a billing error: invoice 55 charged $12 too much. To save space, the app replaces older messages with a short summary. Afterwards the agent mentions the $12 in a reply about the late order and no longer knows the promised date. The fix must keep the exact amounts and dates of both problems correct for the rest of the chat. What is the best fix?

A. Switch to a model that can see more text at once, so older messages never need summarizing.
B. Keep a short fixed note for each problem (its number, amount, date, status), sent unchanged with every message and never summarized.
C. Ask for longer, more detailed summaries.
D. Add an instruction telling the agent to be careful with amounts and dates.

**Q2 [5.1]** In a research system, a main agent combines reports from eight helper agents into one long text, then writes a final answer. The reports are similar in length. The final answer keeps missing an important warning found in reports 4 and 5, but it uses findings from reports 1 and 8. All eight reports must stay together in one input so the main agent can compare them. What is the best change?

A. Add the instruction "read every report carefully" at the top.
B. Send each report to the main agent separately and join the eight answers.
C. Ask each helper to write longer reports so warnings stand out.
D. Put a short summary of key findings at the start of the input, and place each full report under its own clear heading.

**Q3 [5.1]** A support agent uses an order lookup tool (an action that fetches an order's details). Each lookup returns 40 pieces of data. For return requests only four matter: order number, status, amount, and whether the order can be returned. After several lookups the agent's working memory is nearly full and its replies get worse. The agent must still be able to look up orders. What is the best fix?

A. Cut each lookup result down to the four needed pieces before it is added to the chat.
B. Remove the lookup tool and ask the customer for the details instead.
C. Summarize the whole chat after every message.
D. Keep all 40 pieces so no information is ever lost.

**Q4 [5.1]** A developer builds a car-insurance quote app on Claude. To save cost, each time the app contacts Claude it sends only the customer's newest message. The customer already gave the car's make, model, and year, but the app keeps asking for the year again. The fix must stop the repeated questions without changing the model. What is the cause and best fix?

A. The model has a bug; wait for it to be fixed.
B. Add "remember earlier answers" to the instructions.
C. Claude keeps no memory between requests, so the app must send the full chat history every time.
D. Turn up the setting that makes replies more random, so the model recalls earlier answers.

**Q5 [5.1]** In a research system, a helper agent sends a writer agent its full notes: 8,000 words of reasoning plus findings. The writer can only take in a small amount of text. It also receives two similar figures from two helpers and cannot tell which is newer or where each came from. The writer must fit everything in its small space and must know when and where each figure came from. What is the best redesign?

A. Helpers send short structured results (key facts, sources, how relevant each is), with the date, source location, and method for each finding.
B. Helpers send their full notes, and the writer picks out what matters.
C. Helpers send one short paragraph with no sources, to keep it small.
D. The writer redoes the research itself.

---

## Task statement 5.2

**Q1 [5.2]** A store's support agent follows a written policy. The policy lets customers get a refund of the difference if the store's own price drops later. It says nothing about matching other stores' prices. A customer politely asks the agent to match a competitor's lower price. The written policy is the agent's only rulebook, and it does not mention competitors at all. What should the agent do?

A. Approve the match, because the policy does not forbid it.
B. Refuse, because the policy only mentions the store's own prices.
C. Escalate (hand the chat to a human), because the policy does not cover this request.
D. Approve it only if the customer sounds upset.

**Q2 [5.2]** A customer writes to a support agent: "Get me a human agent now." The problem is a simple address change the agent could make in one step. The customer has clearly asked for a person. What should the agent do?

A. Escalate (hand the chat to a human) right away, without first trying to fix the problem.
B. Make the address change first, then offer a human if the customer is still unhappy.
C. Ask the customer to explain the problem so the agent can judge whether a human is needed.
D. Check how confident the model says it is, and escalate only if that is low.

**Q3 [5.2]** A customer writes to a support agent: "This is so annoying, my order is three days late!" The customer has not asked for a person, and checking the order's status is something the agent can do itself. What is the best response?

A. Escalate (hand the chat to a human) right away, because the customer is upset.
B. Ignore the tone and reply only with the tracking number.
C. Tell the customer the agent cannot help with late orders.
D. Say it understands the frustration, offer to check and fix the order, and escalate only if the customer asks again for a person.

**Q4 [5.2]** A support agent hands chats to a human when a sentiment score (a rating of how upset a message sounds) is negative, or when the model rates its own confidence as low. Calm customers with real policy problems are not handed over, while angry customers with easy questions are. The team wants a rule that catches calm customers with policy problems and lets the agent solve easy questions from angry customers. What is the best change?

A. Lower the sentiment score limit so more messages are handed over.
B. Write clear handover rules in the agent's standing instructions (customer asks for a person, policy does not cover it, no progress possible), with a few short worked examples of hand over versus solve.
C. Ask the model to rate its own confidence more carefully.
D. Hand over every case that needs more than three lookups or actions.

**Q5 [5.2]** A support agent searches for a customer by name. The search returns two accounts, both named "Maria Lopez". The customer wants a refund. The refund must go to the right person's account. What should the agent do?

A. Pick the account with the most recent activity, because it is most likely correct.
B. Pick the first account in the list.
C. Ask the customer for another detail, such as an email or order number, before acting.
D. Refund both accounts to be safe.
