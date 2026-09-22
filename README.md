<div align="center">

# 📘 Claude Certified Architect — Foundations

### An unofficial study course, shipped with its receipts

![Modules](https://img.shields.io/badge/10%20Modules-30%20lessons-2EA043?style=for-the-badge)
&nbsp;
![Coverage](https://img.shields.io/badge/Coverage-240%2F240%20exam%20bullets-6E40C9?style=for-the-badge)
&nbsp;
![Audit](https://img.shields.io/badge/Audit%20trail-11%20verdict%20files-FF6F61?style=for-the-badge)
&nbsp;
[![Generated with Claude](https://img.shields.io/badge/Generated%20with-Claude%20Code-D97757?style=for-the-badge&logo=anthropic&logoColor=white)](https://claude.com/claude-code)

[**Start here**](#start-here) · [**The modules**](#the-modules) · [**How to check it**](#how-to-check-it) · [**How it was made**](#how-it-was-made) · [**Limitations**](#limitations)

</div>

---

> **Unofficial.** This is not produced, endorsed, or reviewed by Anthropic. The official exam guide
> is the authority on what is tested; where this course and the exam guide disagree, the exam guide
> is right. Use this as study material, not as a substitute for the real documentation.

A complete study course for the **Claude Certified Architect – Foundations (CCAR-F)** exam:
10 modules, 30 lessons, one lesson per exam task statement, with a quiz and a hands-on exercise
attached to each.

What makes it unusual is not the course. It is that **you do not have to take its word for
anything.** The `runs/` folder ships alongside it: the domain map, the per-domain research, and
eleven evaluation verdict files recording what was checked, what passed, what failed, and why.

## Start here

1. Read [`courses/claude-certified-architect-foundations/course-outline.md`](courses/claude-certified-architect-foundations/course-outline.md)
   — the module → domain → task-statement map, and the reasoning behind the teaching order.
2. Work through the modules in order. Sequencing is deliberate: every concept's prerequisites are
   taught at an earlier module than the concept itself.
3. Each module folder holds three files:

   | File | What's in it |
   |------|--------------|
   | `lesson.md` | Concept explanations with examples, in teaching order |
   | `quiz.md` | That module's quizzes, answers marked |
   | `exercises.md` | One hands-on exercise for the module |

## The modules

| # | Module | Exam domain (weight) | Task statements |
|---|--------|----------------------|-----------------|
| 1 | The Agentic Loop and Multi-Agent Orchestration | Agentic Architecture & Orchestration (27%) | 1.1 – 1.3 |
| 2 | Workflow Enforcement, Decomposition, and Sessions | Agentic Architecture & Orchestration (27%) | 1.4 – 1.7 |
| 3 | Tool Design & MCP Integration | Tool Design & MCP Integration (18%) | 2.1 – 2.5 |
| 4 | Claude Code Memory and Configuration | Claude Code Configuration & Workflows (20%) | 3.1 – 3.3 |
| 5 | Claude Code Execution Modes and CI/CD Workflows | Claude Code Configuration & Workflows (20%) | 3.4 – 3.6 |
| 6 | Precision Prompting and Structured Output Enforcement | Prompt Engineering & Structured Output (20%) | 4.1 – 4.3 |
| 7 | Extraction Quality, Batching, and Review Architectures | Prompt Engineering & Structured Output (20%) | 4.4 – 4.6 |
| 8 | Context Management and Escalation Design | Context Management & Reliability (15%) | 5.1 – 5.2 |
| 9 | Error Propagation and Codebase Context | Context Management & Reliability (15%) | 5.3 – 5.4 |
| 10 | Human Review, Confidence Calibration, and Provenance | Context Management & Reliability (15%) | 5.5 – 5.6 |

Modules are grouped by domain but split where a domain is large, so no module runs longer than five
lessons. Domain 1 is taught first because the agentic loop and the coordinator–subagent architecture
are load-bearing for everything after them — not because it carries the heaviest exam weight.

## How to check it

This is the part worth knowing about. Three claims are made about this course, and all three can be
checked from what is in this repo.

**1. Nothing was dropped.** The exam guide enumerates 240 `Knowledge of:` / `Skills in:` bullets
across 30 task statements. Every one was given a stable ID at the mapping stage and cited through to
the course outline's bullet-to-lesson table. The check is a set comparison in both directions —
nothing in the guide missing from the course, nothing in the course invented:

```
bullet IDs in domain-map    : 240
bullet IDs cited in outline : 240
in map but not outline      : 0
in outline but not map      : 0
```

**2. Every claim traces to a source.** Concepts carry the source they came from, and those citations
were verified by fetching the pages and searching them — not by trusting that the URL looked
official. No concept in this course is marked `UNSOURCED`.

**3. The checking itself is on the record.**
[`runs/.../evaluations/`](runs/claude-certified-architect-foundations/evaluations) holds one verdict
file per stage per round — eleven in total. Each lists every checklist item with an evidence column,
including the ones that passed, plus a separate `Not checked` section stating what was *not*
verified. A file recording only failures would be no evidence the rest was examined.

Three of those rounds came back **REWORK**, all for the same reason: citation faithfulness. Real,
official, on-topic pages carrying claims that were not actually on them. Open
[`domain-researcher-tool-design-mcp-integration-round-1.md`](runs/claude-certified-architect-foundations/evaluations/domain-researcher-tool-design-mcp-integration-round-1.md)
and then the round-2 file to see one caught and corrected.

## How it was made

Generated by [**Certification Trainer**](https://github.com/TarikJID/certification-trainer), a
multi-agent pipeline that maps a certification's domains, researches each one in parallel, and
assembles a sequenced course — with an evaluator between every stage rather than one check at the
end.

```
runs/claude-certified-architect-foundations/
  sources/       the exam guide, archived as fetched
  domain-map.md  domains, task statements verbatim, bullet IDs
  dispatch/      the per-domain slice each researcher was given
  research/      one file per domain — concepts, prerequisites, sources
  evaluations/   11 verdict files, one per stage per round
```

Paths inside the verdict files are relative to this repo root, so every citation in them resolves
against the files shipped here.

## Work in progress — no tutor yet

Right now this is **material you read yourself.** Open a `lesson.md`, work the quiz, do the
exercise, mark your own answers.

What's planned and not yet built is an **interactive tutor**: a `CLAUDE.md` plus skills shipped
inside this repo, so you could open the folder in [Claude Code](https://claude.com/claude-code) and
be taught through it one concept at a time — checked for understanding as you go, with your progress
tracked across sessions rather than restarting each time.

Until then, treat the quizzes as self-assessment. The answers are marked in `quiz.md`, so the
"never reveal before an attempt" discipline is on you, not on the repo.

## Limitations

Read these before relying on it.

- **Unofficial and unreviewed.** No Anthropic involvement. The official exam guide wins any
  disagreement.
- **Coverage is not quality.** Every exam bullet has a lesson and every citation held up under
  checking. Whether the course *teaches well* is a separate question that no automated check in this
  repo answers.
- **Written by agents.** Verify anything you intend to rely on. The audit trail exists so that you
  can, and the sources are cited so you know where to look.
- **A snapshot.** Certifications change. This reflects the exam guide as fetched at generation time;
  the archived copy is in `runs/.../sources/` so you can tell whether it has moved since.

---

<div align="center">

Built with [Certification Trainer](https://github.com/TarikJID/certification-trainer) ·
Not affiliated with Anthropic

</div>
