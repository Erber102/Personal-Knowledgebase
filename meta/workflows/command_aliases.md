---
title: "Command Aliases — Dispatch Table"
type: workflow
created: 2026-05-10
updated: 2026-05-12
---

# Command Aliases — Dispatch Table

Match on intent, not exact phrasing. If the command may modify files, first state planned reads/writes and ask for confirmation unless the user explicitly says to execute.

---

## Intent-Matching Rules

- "后面再看" / "暂时不想看懂" → **Parking Ingest**, not Full Paper Ingest.
- "学习" / "带我读" / "看懂" → **Paper Learning** (Reading Mission + Paper Spine first), then ask whether to enter Socrates Mode.
- "教我" / "带我学" → **Course or Socrates teaching flow**, not just ingest.
- "逃课" / "补课" → **Catch-up Session**; start with diagnostic test and prerequisite tree.
- "考我" → **Examiner Mode**; do not give answers before the user attempts.
- Never modify `raw/`.

---

## Dispatch Table

### Research

| # | Trigger Phrases | Workflow File | Section |
|---|---|---|---|
| ① | "ingest 这篇论文，我后面再看" · "先放进系统，后面再读" · "暂时不想看懂" | `meta/workflows/research.md` | Parking Ingest |
| ② | "我想学习这篇论文" · "带我读这篇论文" · "帮我看懂这篇论文" · "learn this paper" | `meta/workflows/research.md` | Paper Learning |
| ③ | "帮我正式 ingest 这篇论文" | `meta/workflows/research.md` | Full Paper Ingest |
| ④ | "帮我判断这个 idea 有没有人做过" | `meta/workflows/research.md` | Novelty Sweep |
| ⑤ | "把这个 idea 放进系统" | `meta/workflows/research.md` | Idea Capture |

### Course

| # | Trigger Phrases | Workflow File | Section |
|---|---|---|---|
| ⑥ | "帮我 ingest 这节课" | `meta/workflows/course.md` | Course Ingest |
| ⑦ | "ingest 这节课然后教我" · "ingest this lecture and teach me" · "整理这节课然后带我学" | `meta/workflows/course.md` | Course Ingest + Teach |
| ⑧ | "我逃课了，帮我补这节" | `meta/workflows/course.md` | Catch-up Session |
| ⑨ | "帮我准备这次作业" | `meta/workflows/course.md` | Homework Preparation |

### Socrates

| # | Trigger Phrases | Workflow File | Section |
|---|---|---|---|
| ⑩ | "用 Socrates 模式问我" | `meta/workflows/socrates.md` | Socrates Session |
| ⑪ | "我觉得我懂了，考我" | `meta/workflows/socrates.md` | Examiner Mode |

### Maintenance

| # | Trigger Phrases | Workflow File | Section |
|---|---|---|---|
| ⑫ | "帮我整理系统" | `meta/workflows/maintenance.md` | Light Lint |
| ⑬ | "帮我记录这次修改" | `meta/workflows/maintenance.md` | Change Log Update |
