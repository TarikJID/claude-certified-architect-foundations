# Module 8 Fast Track: Context and Escalation

## 5.1 Manage conversation context across long interactions

**Exam rule:** Long chats lose details. Keep key facts safe, keep inputs small, put important things first.

- Summaries blur exact amounts, dates, order numbers. Pick: a "case facts" block sent verbatim every turn, outside the summary. Several issues: one block per issue.
- Tool results pile up. Pick: trim to the needed fields before they enter context.
- Models miss the middle of long inputs. Pick: key-findings summary at the start, section headers below.
- The API is stateless. Pick: send the full history every request.
- Subagent feeding another agent: return compact structured data (facts, citations, relevance) plus dates and source info. Reject: full reasoning text.
- Trap: "bigger context window" or "summarize harder". Neither saves the exact details.

**Example:** Order lookup returns 40 fields. Keep order ID, status, amount, return-eligible. Drop the rest.

## 5.2 Design escalation and ambiguity resolution

**Exam rule:** Escalate on a clear trigger, not on a feeling. Ask when unsure who the customer is.

- Three triggers: customer asks for a human; policy is silent or an exception is needed; no progress is possible.
- Explicit request for a human: escalate now. No investigating first.
- Frustrated but no request, and the issue is simple: acknowledge, offer to fix it. Escalate if they repeat the request.
- Policy silent (for example, competitor price match): escalate. Silence is not permission.
- Several customer matches: ask for another identifier. Never pick the most recent or first.
- Trap: sentiment score or the model's own confidence as the trigger. Both are unreliable. Best fix: explicit criteria with few-shot examples in the system prompt.

**Example:** Five tool calls, clean policy fit: do not escalate. Complexity alone is not a trigger.
