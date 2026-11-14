# CCAR-F Final Practice Exam (Readiness Check)

Format: 20 multiple-choice questions, 4 scenarios (5 questions each), one best answer per question. Take it after Modules 6-10. Source: CCAR-F Exam Guide v1.0 (task statements cited per question). Answers are in a separate file.

---

## Scenario 1: Customer Support Resolution Agent

You are building a customer support resolution agent with the Claude Agent SDK. It handles returns, billing disputes and account issues through custom MCP tools (get_customer, lookup_order, process_refund, escalate_to_human). The target is 80%+ first-contact resolution while escalating at the right moments. Human agents who receive escalations cannot see the conversation transcript.

### Question 1 [Task 1.5]
Company policy says refunds above $500 need human approval. The system prompt already states this rule, yet an audit found a few $620 refunds issued by the agent. What is the best fix?

A. Rewrite the system prompt with the rule in capital letters and add three few-shot examples of refusing large refunds.
B. Add a hook that intercepts outgoing process_refund calls, blocks amounts above $500, and redirects to the human escalation workflow.
C. Lower the agentic loop's maximum iteration count so the agent has fewer chances to reach process_refund.
D. Have the agent report a confidence score before each refund and proceed only when the score is high.

### Question 2 [Task 2.2]
A customer asks to return an item bought 90 days ago; the return window is 30 days. process_refund currently returns the text "Operation failed", and the agent retries three times before apologising vaguely. Which change best fixes this?

A. Raise the retry limit so the agent tries more times before giving up.
B. Return an empty result marked as success so the agent moves on to another topic.
C. Set tool_choice to "any" so the agent must call a different tool.
D. Return an error flagged with isError, a business-error category, a non-retryable marker, and a customer-friendly explanation of the policy.

### Question 3 [Task 5.2]
A customer writes, "Stop. I want a human agent now." The question is a simple order-status check that the agent could answer in one lookup. What should the agent do?

A. Honor the request immediately and escalate with a structured handoff, without first investigating.
B. Do the order lookup first, then escalate only if the customer is still unhappy with the answer.
C. Acknowledge the frustration, offer to resolve the status question, and escalate only if the customer repeats the request.
D. Ask the model for a self-reported confidence score and escalate only if it is low.

### Question 4 [Task 1.4]
The agent escalates a billing dispute mid-process. The human agent has no access to the conversation transcript. What should the handoff contain?

A. Only the customer's most recent message, so the human starts fresh.
B. A ticket link and a note saying the customer seems upset.
C. A structured summary: customer ID, root cause, refund amount, and recommended action.
D. Raw dumps of every tool response gathered during the session.

### Question 5 [Task 5.1]
After 15 turns, the agent forgets the exact refund amount and the delivery date the customer stated earlier. Each lookup_order call returns 40+ fields, of which only about five matter for returns. Which approach best addresses this?

A. Summarise the whole history more aggressively into short prose each turn.
B. Keep transactional facts (amounts, dates, order numbers, statuses) in a persistent case-facts block in every prompt, and trim lookup results to the return-relevant fields.
C. Place the customer's key statements in the middle of a long prompt so they are surrounded by context.
D. Send only the latest customer message on each request to keep the context small.

---

## Scenario 2: Code Generation with Claude Code

Your team uses Claude Code for code generation, refactoring, debugging and documentation. You are standardising its use with CLAUDE.md files, custom slash commands and skills, and deciding when to use plan mode versus direct execution. The repository is a large monorepo with test files scattered across many directories.

### Question 6 [Task 3.1]
A newly hired developer's Claude Code ignores the team's testing conventions, while a senior developer's Claude Code follows them. Investigation shows the senior developer wrote the conventions in their own ~/.claude/CLAUDE.md. What is the right fix?

A. Move the conventions into the project-level CLAUDE.md (root or .claude/) so they are shared through version control.
B. Ask the new developer to copy the senior developer's personal file into their own home folder.
C. Put the conventions in ~/.claude/commands/ so every teammate receives them.
D. Add the conventions to every subdirectory's CLAUDE.md and ask each person to re-read them.

### Question 7 [Task 3.3]
The team wants a convention applied only to files matching **/*.test.tsx, which live in dozens of different directories. They want the rule loaded only when such files are being edited. What is the best approach?

A. Create a CLAUDE.md in every directory that contains test files.
B. Put the convention in the root CLAUDE.md so it is always loaded.
C. Create a skill and have developers invoke it by hand before editing tests.
D. Create a file in .claude/rules/ with YAML frontmatter whose paths field holds the glob pattern.

### Question 8 [Task 3.4]
Which assignment of approach to task is best?

A. Plan mode for a single-file bug fix with a clear stack trace; direct execution for a library migration touching 45+ files.
B. Plan mode for a library migration touching 45+ files, then direct execution of the agreed plan; direct execution for adding a date validation conditional to one function.
C. Direct execution for both, because plan mode only slows down experienced developers.
D. Plan mode for both, to be consistent across the team.

### Question 9 [Task 3.2]
A team skill analyses the whole codebase and prints very long reports, flooding the developer's main conversation. How should the skill be configured?

A. Move its instructions into CLAUDE.md so they are always loaded.
B. Add allowed-tools to the SKILL.md frontmatter so it can use fewer tools.
C. Set context: fork in the SKILL.md frontmatter so it runs in an isolated sub-agent context.
D. Copy it to ~/.claude/commands/ so it is personal to each developer.

### Question 10 [Task 1.7]
Yesterday you ran a named investigation session on the repository. Overnight, a teammate changed three of the files the session had analysed. Most of the prior analysis is still valid. What is the best way to continue?

A. Discard the session and re-explore the whole repository from scratch.
B. Use fork_session to branch, since forking refreshes stale file contents automatically.
C. Resume the session by name and say nothing, trusting Claude to notice the changes.
D. Resume the session by name and tell it which three files changed so it re-analyses only those.

---

## Scenario 3: Multi-Agent Research System

You are building a multi-agent research system with the Claude Agent SDK. A coordinator delegates to specialised subagents: web search, document analysis, synthesis, and report generation. The system produces comprehensive reports with citations on broad topics.

### Question 11 [Task 1.3]
The web-search and document-analysis subagents work on independent subtopics, yet total latency is high because the coordinator spawns them one per turn. What is the best change?

A. Let the two subagents message each other directly to coordinate.
B. Raise the maximum number of loop iterations for the coordinator.
C. Have the coordinator emit multiple Task tool calls in a single response so the subagents run in parallel.
D. Merge both roles into a single subagent with a longer system prompt.

### Question 12 [Task 1.2]
For the topic "the impact of AI on creative industries", the final report covers only visual arts. The logs show the coordinator assigned subtopics such as "AI in digital art", "AI in graphic design" and "AI in photography", and each subagent completed its task well. What is the most likely root cause?

A. The coordinator decomposed the topic too narrowly, leaving music, writing and film uncovered.
B. The web-search subagent's tool descriptions are too short.
C. The synthesis subagent dropped sections during summarisation.
D. The document-analysis subagent has too many tools.

### Question 13 [Task 2.3]
The synthesis subagent keeps attempting its own web searches, and most of its extra calls are quick fact checks. What is the best design?

A. Give every subagent the full tool set so none is ever blocked.
B. Add a prompt line saying "never search the web" and keep all tools available.
C. Remove the synthesis subagent and let the coordinator write the report.
D. Restrict the synthesis subagent to role-relevant tools plus a narrow scoped verify_fact tool, routing complex lookups through the coordinator.

### Question 14 [Task 5.6]
Two credible sources give different market-size figures for the same sector: one report published in 2022 and another in 2024. What should the synthesis output do?

A. Report the higher figure, since it is more favourable to the narrative.
B. Include both values with source attribution and publication dates, so a temporal difference is not mistaken for a contradiction.
C. Average the two numbers into a single figure.
D. Drop both values and state that the data is unreliable.

### Question 15 [Task 2.1]
Two tools, analyze_content and analyze_document, have near-identical descriptions, and the agent often picks the wrong one. Which fix is best?

A. Add a system prompt rule that routes any request containing the word "analyze" to analyze_document.
B. Force tool_choice to analyze_document for every request.
C. Rename analyze_content to something web-specific such as extract_web_results and rewrite its description to state its purpose, inputs and boundaries.
D. Increase max_tokens so the model has room to think about which tool to choose.

---

## Scenario 6: Structured Data Extraction

You are building a system that extracts information from unstructured documents (invoices, receipts and contracts), validates the output with JSON schemas, and feeds downstream systems. It must handle edge cases gracefully and maintain high accuracy. Document types are not known in advance.

### Question 16 [Task 4.3]
Many invoices have no purchase-order number. The extraction schema marks po_number as required, and the model sometimes returns plausible but invented values. What is the best fix?

A. Retry every invoice that returns a suspicious value until a different value appears.
B. Make po_number an optional (nullable) field so the model can return null when the document does not contain it.
C. Add the instruction "be conservative and only report high-confidence values" to the prompt.
D. Keep the field required but lengthen the field description.

### Question 17 [Task 4.4]
Validation fails on a contract because the customer tax ID is missing. The extraction tool was given only the contract; the tax ID exists in a separate attachment that was never supplied. Which statement is correct?

A. Retrying with the error appended will not help because the information is absent from the source; supply the missing document or leave the field null and route to review.
B. Retry with the validation error appended up to five times; repetition eventually surfaces the value.
C. Reword the prompt more forcefully so the model searches harder for the value.
D. Switch tool_choice to "any" so the model finds the value in another tool.

### Question 18 [Task 4.5]
Two workloads exist. Workload one: a customer uploads a document and waits for the extracted result on screen. Workload two: an overnight backfill of thousands of archived documents where a result within 24 hours is acceptable. Which pairing is best?

A. Message Batches API for both, to maximise cost savings.
B. Synchronous API for both, to keep the design simple.
C. Message Batches API for the waiting customer, synchronous API for the backfill.
D. Synchronous API for the waiting customer, Message Batches API for the overnight backfill.

### Question 19 [Task 2.3]
The system has separate extraction tools for invoices, receipts and contracts. The document type is unknown up front, and sometimes the model replies with conversational text instead of calling a tool. Which tool_choice setting best guarantees structured output?

A. "auto", so the model can decide freely.
B. Forced selection of the invoice extraction tool.
C. "any", so the model must call a tool but can choose which one.
D. No tool_choice, and parse the conversational text with a regular expression.

### Question 20 [Task 4.4]
Every extraction passes schema validation, yet some invoices have line items that do not add up to the stated total. What is the best response?

A. Add a calculated_total field alongside stated_total so discrepancies can be detected and flagged for follow-up.
B. Enable strict schema mode, which will prevent the mismatch.
C. Ask the model to output free-form prose instead of JSON.
D. Mark more fields as required so the model pays closer attention.
