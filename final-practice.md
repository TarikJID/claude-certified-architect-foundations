# CCAR-F Final Practice Exam (Readiness Check)

Format: 20 multiple-choice questions in 4 scenarios (5 questions each). Pick the one best answer, A to D. Take it after Modules 6-10. Each question shows the exam objective it tests in brackets, for example [Task 1.5]. All facts come from the CCAR-F Exam Guide v1.0. The answers are in a separate file.

How to read each question: the setup says what the system is and what each piece of data means. The line starting "Deciding constraint:" is the fact that decides the answer.

---

## Scenario 1: Customer Support Resolution Agent

A company runs an AI support agent: a program built on Claude that chats with customers and can take actions for them. It handles returns, billing disputes and account problems. It acts through four tools, which are functions it can call on the company's systems: get_customer (looks up who the customer is), lookup_order (fetches an order's details), process_refund (sends money back) and escalate_to_human (passes the case to a human support worker). The goal is to solve at least 80% of cases in the first conversation, and to hand over to a human at the right moments. The human workers who receive a handover cannot see the chat that came before it.

### Question 1 [Task 1.5]
Company policy: refunds above $500 need a human's approval. The system prompt, which is the standing instruction text the agent reads before every conversation, already states this rule. Even so, an audit found a few $620 refunds that the agent issued on its own.

Deciding constraint: the $500 limit must hold every single time, with no exceptions.

What is the best fix?

A. Rewrite the rule in the system prompt in capital letters and add three worked examples of the agent refusing large refunds.
B. Add a hook, a small piece of code that checks every refund request before it is carried out, which blocks any refund above $500 and sends the case to a human instead.
C. Lower the maximum number of steps the agent may take per conversation, so it has fewer chances to reach the refund tool.
D. Have the agent rate its own confidence before each refund, and allow the refund only when it rates itself highly.

### Question 2 [Task 2.2]
A customer asks to return an item bought 90 days ago. Company policy only allows returns within 30 days. When process_refund refuses, all it sends back to the agent is the text "Operation failed". The agent cannot tell why it failed, so it tries the same refund three more times and then gives the customer a vague apology.

Deciding constraint: this refusal is a policy rule, so retrying can never succeed, and the customer deserves a clear reason.

Which change to the refund tool's reply best fixes this?

A. Let the agent retry more times before giving up.
B. Make the tool report an empty result as if it had succeeded, so the agent moves on to another topic.
C. Change a setting so the agent is forced to call some tool on every turn.
D. Make the tool send back a clearly marked error that says what kind of error it is (a policy refusal), says that retrying will not help, and includes a plain explanation the agent can pass on to the customer.

### Question 3 [Task 5.2]
A customer writes: "Stop. I want a human agent now." The customer's actual question is simple: where is my order? The agent could answer it with one order lookup.

Deciding constraint: the customer has explicitly asked for a human.

What should the agent do?

A. Hand over to a human straight away, with a summary of the case, without investigating first.
B. Look up the order first, and hand over only if the customer is still unhappy with the answer.
C. Acknowledge the frustration, offer to answer the order question, and hand over only if the customer asks for a human again.
D. Have the agent rate its own confidence, and hand over only if that rating is low.

### Question 4 [Task 1.4]
Partway through a billing dispute, the agent hands the case to a human support worker.

Deciding constraint: the human worker cannot see any of the earlier chat, so the handover note is all they get.

What should the handover note contain?

A. Only the customer's most recent message, so the human starts fresh.
B. A link to the support ticket and a note saying the customer seems upset.
C. A structured summary: the customer's ID, the root cause of the problem, the refund amount at stake, and the recommended next action.
D. A full copy of every raw reply the tools returned during the conversation.

### Question 5 [Task 5.1]
After 15 back-and-forth messages, the agent forgets two facts the customer stated early on: the exact refund amount and the delivery date. Part of the reason is volume: every order lookup returns more than 40 pieces of information about the order, and only about five of them matter for a return. All of it piles up in the agent's working memory of the conversation, called its context.

Deciding constraint: exact numbers and dates must survive a long conversation, and the agent's memory space is limited.

Which approach best fixes this?

A. Shorten the whole conversation history into a brief prose summary after every turn.
B. Keep a "case facts" block (amounts, dates, order numbers, statuses) that is included in full with every message to the agent, and cut each order lookup down to the five fields that matter for returns.
C. Place the customer's key statements in the middle of a long message to the agent, so they are surrounded by supporting detail.
D. Send the agent only the customer's latest message each time, to keep its memory small.

---

## Scenario 2: Code Generation with Claude Code

A software team uses Claude Code, an AI coding assistant that runs in a developer's terminal and can read, write and change the team's code. They use it to write new code, restructure existing code, fix bugs and write documentation. The team is setting it up with shared instruction files and reusable commands. A command is a saved set of instructions a developer runs by typing a slash and its name, for example /review. Commands kept in the project's .claude/commands/ folder are shared with the whole team; commands kept in a developer's personal commands folder (~/.claude/commands/, in their home folder) are for that developer only. The team is also deciding when Claude should plan before acting. The code lives in one very large shared repository (the project's folder of code, stored in version control so the whole team gets the same files). Test files, which are code that checks other code works, are spread across many folders.

### Question 6 [Task 3.1]
Claude Code reads standing instructions from files called CLAUDE.md. A file in a developer's personal home folder (~/.claude/CLAUDE.md) applies only to that developer. A CLAUDE.md inside the project folder is shared with everyone through version control. A senior developer wrote the team's testing rules in their personal file. Their Claude follows the rules; a new hire's Claude ignores them.

Deciding constraint: the rules must reach every team member automatically, including future hires.

What is the right fix?

A. Move the testing rules into the project-level CLAUDE.md, so they are shared through version control.
B. Ask the new hire to copy the senior developer's personal file into their own home folder.
C. Put the rules in the personal commands folder (~/.claude/commands/) so every teammate receives them.
D. Paste the rules into a separate CLAUDE.md in every folder and ask each person to reread them.

### Question 7 [Task 3.3]
The team has a rule that applies only to test files whose names end in ".test.tsx". These files sit in dozens of different folders. A pattern like **/*.test.tsx, called a glob, matches "any file ending in .test.tsx, in any folder".

Deciding constraint: the rule should be loaded only while Claude is editing one of those test files, and not at any other time, so it does not waste Claude's limited memory.

What is the best approach?

A. Create a separate CLAUDE.md in every folder that contains test files.
B. Put the rule in the main project CLAUDE.md, which is loaded all the time.
C. Package the rule as a skill (a reusable add-on a developer starts by hand) and ask developers to start it before editing tests.
D. Create a rule file in the .claude/rules/ folder whose header lists the pattern **/*.test.tsx in a "paths" field, so it loads only when a matching file is being edited.

### Question 8 [Task 3.4]
Claude Code can work in two ways. In plan mode it first explores the code and proposes a plan, changing nothing until the plan is agreed. In direct execution it makes the change straight away. The team has two tasks: (1) switching to a new library, a shared package of code, which touches more than 45 files; (2) adding one date check to a single function.

Deciding constraint: plan first only where the change is large or has several reasonable approaches; for a small, clear change, planning is wasted effort.

Which assignment is best?

A. Plan mode for the single date check; direct execution for the 45-file library switch.
B. Plan mode for the 45-file library switch, then carry out the agreed plan directly; direct execution for the single date check.
C. Direct execution for both, because planning only slows experienced developers down.
D. Plan mode for both, so the team is consistent.

### Question 9 [Task 3.2]
The team has a skill, a reusable add-on stored in a file called SKILL.md, that analyses the whole codebase and prints very long reports. The reports flood the developer's main conversation with Claude and push out what they were working on. The header of SKILL.md can hold settings such as "context: fork" (run the skill in its own separate side conversation and return only the result) and "allowed-tools" (limit which tools the skill may use).

Deciding constraint: the long output must stay out of the main conversation.

How should the skill be configured?

A. Move the skill's instructions into CLAUDE.md, so they are always loaded.
B. Add "allowed-tools" to the skill's header, so it can use fewer tools.
C. Add "context: fork" to the skill's header, so it runs in its own separate side conversation.
D. Copy the skill into each developer's personal commands folder.

### Question 10 [Task 1.7]
Yesterday a developer ran a long investigation of the code in a Claude session, a saved conversation that can be reopened by its name. Overnight a teammate changed three of the files that session had analysed. Everything else the session learned is still correct. Two tools exist: "resume", which reopens a saved session by name, and "fork", which copies a session into a new, separate branch so two different approaches can be tried side by side.

Deciding constraint: most of yesterday's analysis is still valid; only three known files have changed.

What is the best way to continue?

A. Throw the session away and re-investigate the whole codebase from scratch.
B. Fork the session, because forking reloads changed files automatically.
C. Resume the session by name and say nothing, trusting Claude to notice the changes.
D. Resume the session by name and tell it exactly which three files changed, so it re-checks only those.

---

## Scenario 3: Multi-Agent Research System

A team builds an AI research system made of several cooperating AI agents. One agent, the coordinator, receives the research question, splits it into parts and hands each part to a specialist agent, called a subagent: one searches the web, one analyses documents, one combines the findings, and one writes the final report. Each agent acts through tools, which are functions it can call, such as one that runs a web search. The coordinator starts each subagent through a tool called Task. The system produces long reports on broad topics, with a source cited for every claim.

### Question 11 [Task 1.3]
The web-search subagent and the document-analysis subagent work on separate, independent parts of the question. Yet the whole job is slow, because the coordinator starts them one at a time: it starts one subagent, waits for its reply, and only then starts the next.

Deciding constraint: the two jobs do not depend on each other, so they could run at the same time.

What is the best change?

A. Let the two subagents message each other directly to coordinate their work.
B. Raise the maximum number of steps the coordinator may take.
C. Have the coordinator issue both Task calls in the same single reply, so both subagents start at once and run in parallel.
D. Merge the two specialists into one subagent with longer instructions.

### Question 12 [Task 1.2]
The question was "the impact of AI on creative industries". The final report covers only visual arts. The logs show the coordinator assigned the subagents three parts: "AI in digital art", "AI in graphic design" and "AI in photography". Each subagent did its assigned part well.

Deciding constraint: the subagents did exactly what they were asked; the gap lies in what they were asked to do.

What is the most likely root cause?

A. The coordinator split the topic too narrowly, so music, writing and film were never assigned to anyone.
B. The descriptions of the web-search subagent's tools are too short.
C. The subagent that combines findings dropped sections while summarising.
D. The document-analysis subagent has too many tools.

### Question 13 [Task 2.3]
The subagent that combines findings keeps trying to run its own web searches, which is the web-search subagent's job. Looking at these extra searches, most are quick checks of a single fact.

Deciding constraint: quick fact checks are frequent and legitimate; full research belongs to the web-search subagent.

What is the best design?

A. Give every subagent every tool, so none is ever blocked.
B. Add a line to its instructions saying "never search the web", but keep all tools available to it.
C. Remove that subagent and let the coordinator write the report.
D. Give that subagent only the tools its role needs, plus one narrow tool, verify_fact, for quick fact checks; anything bigger goes back through the coordinator.

### Question 14 [Task 5.6]
Two trustworthy sources give different market-size figures for the same industry. One is a report published in 2022, the other a report published in 2024.

Deciding constraint: both sources are credible, and the difference may simply be because they measured two years apart.

What should the final report do?

A. Report the higher figure, because it fits the report's story better.
B. Include both figures, each with its source and publication date, so readers can see the difference may be a change over time rather than a contradiction.
C. Average the two figures into one number.
D. Leave out both figures and say the data is unreliable.

### Question 15 [Task 2.1]
An agent chooses which tool to use mainly by reading each tool's name and description. Two tools, analyze_content and analyze_document, have almost identical descriptions, and the agent often picks the wrong one. In fact analyze_content is meant only for web search results.

Deciding constraint: both tools are needed, and the agent must be able to tell them apart from what it reads about them.

Which fix is best?

A. Add a line to the agent's instructions sending every request that contains the word "analyze" to analyze_document.
B. Force the agent to use analyze_document for every request.
C. Rename analyze_content to something web-specific, such as extract_web_results, and rewrite its description to say what it is for, what input it takes and when not to use it.
D. Allow the agent longer replies, so it has more room to think about which tool to pick.

---

## Scenario 6: Structured Data Extraction

A company builds a system that reads business documents (invoices, receipts and contracts) and pulls out specific pieces of information, such as totals, dates and ID numbers. It fills these into a fixed form with named fields. A schema defines that form: which fields exist, what type each one is, and whether each must be filled in ("required") or may be left empty ("optional"). Claude fills the form by calling a tool, a function it can call whose input is the form defined by the schema. The filled form is checked against the schema and then passed to other business systems. Document types are not known in advance.

### Question 16 [Task 4.3]
The schema marks the field po_number (the purchase-order number) as required. Many invoices simply do not have one. For those invoices, Claude sometimes fills in a believable but made-up number.

Deciding constraint: when a value is not in the document, the system must say so, not invent one.

What is the best fix?

A. Retry every invoice with a suspicious value until a different value comes back.
B. Make po_number optional and allowed to be empty (null), so Claude can return "no value" when the invoice has none.
C. Add "be conservative and only report high-confidence values" to the instructions.
D. Keep po_number required but write a longer description of the field.

### Question 17 [Task 4.4]
The check fails on a contract because the customer's tax ID field is empty. Claude was given only the contract itself. The tax ID appears in a separate attachment that was never given to Claude. The system can retry, meaning send the request again with the error message added.

Deciding constraint: the missing value is not anywhere in what Claude was given.

Which statement is correct?

A. Retrying with the error added will not help, because the value is not in the source; supply the missing attachment, or leave the field empty and send the case to a person for review.
B. Retry with the error added up to five times; repetition will eventually produce the value.
C. Reword the instructions more forcefully so Claude searches harder for the value.
D. Change a setting that forces Claude to call some tool, so it finds the value through another tool.

### Question 18 [Task 4.5]
There are two jobs. Job one: a customer uploads a document on the website and waits on screen for the result. Job two: overnight, thousands of archived documents must be processed, and results any time within 24 hours are fine. There are two ways to send work to Claude. The standard way answers each request right away. The Message Batches API takes a large bundle of requests, costs 50% less, and returns results within 24 hours, with no promise of how soon.

Deciding constraint: one job has a person waiting; the other can wait up to a day.

Which pairing is best?

A. Batches for both jobs, to save the most money.
B. The standard way for both jobs, to keep the design simple.
C. Batches for the waiting customer; the standard way for the overnight job.
D. The standard way for the waiting customer; batches for the overnight job.

### Question 19 [Task 2.3]
The system has three separate extraction tools: one for invoices, one for receipts, one for contracts. Each fills in a different form. A setting called tool_choice controls whether Claude must use a tool: "auto" lets Claude choose to reply in plain text instead; "any" means Claude must call one of the tools but chooses which; forcing a named tool means Claude must call that exact tool. Right now Claude sometimes replies in plain text instead of filling any form.

Deciding constraint: Claude must always fill a form, but the document type is unknown, so it must still be free to pick the right one of the three.

Which setting is best?

A. "auto", so Claude decides freely.
B. Force the invoice tool every time.
C. "any", so Claude must call a tool but can choose which one.
D. No setting at all, and pull the values out of Claude's plain-text reply with a text-matching script.

### Question 20 [Task 4.4]
Every filled invoice form passes the schema check: every field is present and has the right type. Yet on some invoices the individual line items do not add up to the total printed on the invoice.

Deciding constraint: the schema check only confirms the form's shape, not whether its numbers agree with each other.

What is the best response?

A. Have Claude also fill in a calculated_total (the line items added up) next to the stated_total (the total printed on the invoice), so mismatches can be spotted and flagged.
B. Turn on strict schema checking (a stricter mode that guarantees the filled form is always well formed, with every field present and of the right type), which will stop the mismatch.
C. Ask Claude for free-form prose instead of a filled form.
D. Mark more fields as required, so Claude pays closer attention.
