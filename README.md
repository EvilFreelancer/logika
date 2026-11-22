# Logika (formal logic)

**Purpose**: Provides the agent with a classical formal-logic framework based on G. Chelpanov's textbook («Учебник логики»). It enables the model to review and fix the logic of Russian texts, perform rigorous logical analysis, construct and evaluate syllogisms, detect logical fallacies, and apply inductive reasoning methods. The Russian reference notes are distilled from the book; an OCR transcript of the complete 1917 edition is bundled in [`source/`](source/).

## Modes

| Mode | How to invoke | What it does |
|------|---------------|--------------|
| **Review** (`logika:review`) | `/logika:review <текст>` (plugin command), or ask: «проверь логику», «логическое ревью», «найди логические ошибки» | Analysis-only report: argument structure, every fallacy named (Russian + Latin), why it is an error, how to fix. The text is **not** rewritten. |
| **Fix** (default) | `/logika` + text, or ask: «исправь логику», «поправь аргументацию» | Short diagnosis, then the text rewritten with corrected reasoning (author's style preserved, minimal edits) + a list of changes. |
| **Problems** | Give a logic textbook problem | Step-by-step solution: check a syllogism, convert a judgment, find the figure/mood, identify Mill's method, restore an enthymeme. |
| **Benchmark** | Only for explicit BQA (yes/no) / MCQA (A/B/C/D) tasks | Single JSON object `{"reasoning": ..., "answer": ...}` for automated grading. |

**When to use**

- Reviewing or fixing the argumentation of a (Russian) text.
- Analyzing arguments or checking the validity of inferences.
- Classifying concepts, judgments, or logical forms; checking definitions and divisions.
- Building or reducing syllogisms, proving statements, or identifying logical errors.
- Applying the laws of thought (identity, non-contradiction, excluded middle, sufficient reason).
- Performing inductive reasoning using Mill's methods, analogies, or hypothesis evaluation.

**Core workflow**

1. Identify the argument structure: thesis, premises, conclusions.
2. Determine the form of each inference (syllogism, conditional, disjunctive, immediate, induction, analogy).
3. Load the appropriate reference files from `references/` and verify each step against the rules.
4. Name every error (Russian + Latin) and produce the mode-specific output: report, fixed text, or solution.

**Reference files** (in Russian, terminology per Chelpanov)

- `references/concepts.md` — понятия: классификация, определение, деление.
- `references/judgments.md` — суждения: A/E/I/O, логический квадрат, распределённость, непосредственные умозаключения.
- `references/syllogism.md` — силлогизм: фигуры и модусы, сведение, условные/разделительные, энтимемы и сориты.
- `references/induction.md` — индукция: методы Милля, гипотеза, аналогия, классификация.
- `references/errors.md` — каталог логических ошибок, софизмы и паралогизмы.
- `references/laws.md` — четыре закона мышления.

**Docs**

- `docs/konspekt.md` — вторичный конспект 26 глав; он не заменяет полный текст издания 1917 года.
- [`source/README.md`](source/README.md) — описание издания, происхождения OCR-текста и пагинации.
- [`source/uchebnik-logiki-chelpanov-1917-9e-ocr.txt`](source/uchebnik-logiki-chelpanov-1917-9e-ocr.txt) — единый OCR-текст 9-го издания 1917 года, все 28 глав.

**Why it matters**

Embedding a structured logical reasoning skill allows the agent to go beyond heuristic pattern matching and produce traceable, rule-based arguments. This improves reliability for tasks that require precise logical validation, such as reviewing argumentative texts, educational tutoring, formal debate assistance, or error-checking of analytical writing.

## Install

This fork is distributed through the **[iqdoctor/rpa-skills](https://github.com/iqdoctor/rpa-skills)** catalog and also installs as a plain **skill folder** (Cursor, OpenAI Codex, Kimi Code CLI, and others).

**As a plugin (Claude Code)** — add the catalog once, then install this skill from it:

```text
/plugin marketplace add iqdoctor/rpa-skills
/plugin install logika@rpa-skills
```

**In Coddy**: its built-in catalog follows the upstream collection and does not include this fork's changes. To use this fork, install it as a plain skill folder in `~/.coddy/skills/logika/`.

**As a plain skill folder** — copy or symlink this repository into a skill root (its `SKILL.md` lives at the repo root):

| Tool          | Path                          |
|---------------|-------------------------------|
| Coddy         | `~/.coddy/skills/logika/`       |
| Claude Code   | `~/.claude/skills/logika/`      |
| Cursor        | `~/.cursor/skills/logika/`      |
| OpenAI Codex  | `~/.codex/skills/logika/`       |
| Kimi Code CLI | `~/.kimi/skills/logika/`        |

The directory name must match the `name` field in `SKILL.md`.

## How to invoke

- **Slash command** — type `/logika` in agent chat; with the plugin installed, `/logika:review` runs the analysis-only mode.
- **`@` context** — attach the skill folder or `SKILL.md` to ground the message in these instructions.
- **Automatic** — the agent may load the skill on its own when your request matches the `description` in `SKILL.md`.

## Source & attribution

Originally published as part of **[EvilFreelancer/rpa-skills](https://github.com/EvilFreelancer/rpa-skills)** — [Pavel Rykov](https://t.me/evilfreelancer)'s agent-skills collection (see [notes on vibe coding](https://t.me/evilfreelancer/1485) and the prompt collection [cursor-vibe-prompts](https://github.com/EvilFreelancer/cursor-vibe-prompts)); this repository is now maintained as [iqdoctor/logika](https://github.com/iqdoctor/logika).

This repository is a fork of [EvilFreelancer/logika](https://github.com/EvilFreelancer/logika), part of [Pavel Rykov's original rpa-skills collection](https://github.com/EvilFreelancer/rpa-skills). The bundled text is an OCR transcript of the 9th edition (1917); provenance, public-domain basis in Russia, and OCR limitations are documented in [`source/README.md`](source/README.md). The repository's MIT license applies to the skill materials, not to the underlying historical text.

Licensed under the MIT License — see [LICENSE](LICENSE).
