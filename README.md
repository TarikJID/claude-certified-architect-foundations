<div align="center">

# 📘 Claude Certified Architect — Foundations

### An unofficial study course, with a tutor built in

![Modules](https://img.shields.io/badge/10%20Modules-30%20lessons-2EA043?style=for-the-badge)
&nbsp;
![Tutor](https://img.shields.io/badge/Interactive%20tutor-included-6E40C9?style=for-the-badge)
&nbsp;
![Coverage](https://img.shields.io/badge/Covers-the%20full%20exam%20guide-FF6F61?style=for-the-badge)
&nbsp;
[![Built with Claude](https://img.shields.io/badge/Learn%20with-Claude%20Code-D97757?style=for-the-badge&logo=anthropic&logoColor=white)](https://claude.com/claude-code)

[**Start here**](#start-here) · [**What you'll be able to do**](#what-youll-be-able-to-do) · [**The modules**](#the-modules) · [**How to study it**](#how-to-study-it) · [**Before you rely on it**](#before-you-rely-on-it)

</div>

---

> **Unofficial.** Not produced, endorsed or reviewed by Anthropic. The official exam guide is the
> authority on what is tested — where this course and the guide disagree, the guide is right.

**This course exists to get you ready to sit the CCAR-F exam and pass it.** That is its only job.

It is built backwards from the official exam guide: every objective the guide lists has a lesson
teaching it, a quiz question testing it, and a place in a sequence designed so nothing arrives
before the thing it depends on. Work through it and you will have covered what the exam actually
tests — not a general tour of the subject that happens to overlap.

## Start here

**With the tutor** — the way this course is meant to be taken:

```
git clone https://github.com/TarikJID/claude-certified-architect-foundations
```

Open the folder in [Claude Code](https://claude.com/claude-code) and type `/start`.

Claude reads the course, asks how you like to learn, and teaches it one concept at a time —
checking you've understood before moving on, and remembering where you got to between sessions.

**Or read it yourself.** Everything is plain markdown. Begin with
[`course-outline.md`](course-outline.md), then work the modules in order.

## What you'll be able to do

This exam is about **designing systems that use Claude** — not about using Claude as a chatbot.
That is the shift the whole course is built around.

By the end you should be able to:

- **Reason about the agentic loop** — what makes it continue, what makes it stop, and why a tool
  result has to be handed back explicitly rather than merely having happened
- **Design a tool an agent can actually pick correctly**, and connect one through MCP
- **Configure Claude Code deliberately** — memory, permissions, execution modes, CI
- **Get structured output you can rely on**, instead of parsing prose and hoping
- **Build for the failure cases** — context running out, errors propagating, knowing when a system
  should stop and ask a human

## The modules

Ten modules, thirty lessons — one per exam objective.

| # | Module | Exam area | Weight |
|---|--------|-----------|--------|
| 1 | The Agentic Loop and Multi-Agent Orchestration | Agentic architecture & orchestration | 27% |
| 2 | Workflow Enforcement, Decomposition, and Sessions | Agentic architecture & orchestration | |
| 3 | Tool Design & MCP Integration | Tool design & MCP integration | 18% |
| 4 | Claude Code Memory and Configuration | Claude Code configuration & workflows | 20% |
| 5 | Claude Code Execution Modes and CI/CD Workflows | Claude Code configuration & workflows | |
| 6 | Precision Prompting and Structured Output Enforcement | Prompt engineering & structured output | 20% |
| 7 | Extraction Quality, Batching, and Review Architectures | Prompt engineering & structured output | |
| 8 | Context Management and Escalation Design | Context management & reliability | 15% |
| 9 | Error Propagation and Codebase Context | Context management & reliability | |
| 10 | Human Review, Confidence Calibration, and Provenance | Context management & reliability | |

**The order is not the exam's order — it's prerequisite order.** The agentic loop comes first
because nearly everything else leans on it: tool design assumes you know how a tool call
round-trips, structured output assumes you know what a tool-use block is, and the reliability
material at the end pulls from every earlier module. So you start on the heaviest-weighted area
*and* the foundation at the same time.

## How to study it

Each module folder holds four files:

| File | What's in it |
|------|--------------|
| `lesson.md` | The teaching — concepts with worked examples, in order |
| `quiz.md` | Questions. No answers in this file, deliberately |
| `quiz-answers.md` | The answers. Attempt first |
| `exercises.md` | One hands-on exercise for the module |

**A note on the quizzes.** Answers sit in a separate file so that attempting a question is a real
attempt. If you use the tutor, it logs your attempt before it opens the answers — and it tracks two
things separately:

- whether you can **use** a concept
- whether you can **name** it cold

Those fail independently. It is common to reason your way to a correct answer and still not be able
to produce the term under exam conditions, and an exam will find whichever one is weak. Tracking
them apart is the point.

## Before you rely on it

- **Unofficial and unreviewed.** No Anthropic involvement. The official exam guide wins any
  disagreement.
- **Written by AI agents**, then checked by other agents. The checking was thorough and it is all on
  the record — but verify anything you intend to lean on. Every concept carries its source.
- **Complete coverage is not the same as good teaching.** Every exam objective has a lesson and
  every citation held up when checked. Whether it *teaches well* is a judgement no automated check
  in this repo makes.
- **A snapshot.** Certifications change. This reflects the exam guide as it was when the course was
  generated, and the copy it was built from is archived in `runs/` so you can tell whether it has
  moved.

---

**How this was built, and how to check any of it for yourself:**
[`PROVENANCE.md`](PROVENANCE.md).
