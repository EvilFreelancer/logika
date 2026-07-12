# Logika (formal logic)

**Purpose**: Provides the agent with a classical formal-logic framework based on G. Chelpanov's textbook («Учебник логики»). It enables the model to review and fix the logic of Russian texts, perform rigorous logical analysis, construct and evaluate syllogisms, detect logical fallacies, and apply inductive reasoning methods. All reference material is in Russian, distilled from the source book (bundled in `source/`).

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

- `docs/konspekt.md` — постатейный конспект всех 26 глав учебника Челпанова: суть, ключевые понятия, приёмы с современными примерами, чек-листы.
- `source/README.md` — полный текст учебника.

**Why it matters**

Embedding a structured logical reasoning skill allows the agent to go beyond heuristic pattern matching and produce traceable, rule-based arguments. This improves reliability for tasks that require precise logical validation, such as reviewing argumentative texts, educational tutoring, formal debate assistance, or error-checking of analytical writing.

## Install

This skill is distributed through the **rpa-skills** catalog (a Claude Code plugin marketplace), and also installs as a plain **skill folder** (Cursor, OpenAI Codex, Kimi Code CLI, and others).

**As a plugin (Claude Code)** — add the catalog once, then install this skill from it:

```text
/plugin marketplace add EvilFreelancer/rpa-skills
/plugin install logika@rpa-skills
```

**As a plain skill folder** — copy or symlink this repository into a skill root (its `SKILL.md` lives at the repo root):

| Tool          | Path                          |
|---------------|-------------------------------|
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

Part of **[rpa-skills](https://github.com/EvilFreelancer/rpa-skills)** — [Pavel Rykov](https://t.me/evilfreelancer)'s agent-skills collection (see [notes on vibe coding](https://t.me/evilfreelancer/1485) and the prompt collection [cursor-vibe-prompts](https://github.com/EvilFreelancer/cursor-vibe-prompts)).

Reference material is distilled from **G. Chelpanov's** classical formal-logic textbook «Учебник логики» (public domain); the full text is bundled in `source/`.

Licensed under the MIT License — see [LICENSE](LICENSE).
