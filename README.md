# Logika (formal logic)

**Purpose**: Provides the agent with a classical formal-logic framework based on G. Chelpanov's textbook («Учебник логики»). It enables the model to review and fix the logic of Russian texts, perform rigorous logical analysis, construct and evaluate syllogisms, detect logical fallacies, and apply inductive reasoning methods. The reference material is in Russian and distilled from the textbook.

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

- [`skills/logika/references/concepts.md`](skills/logika/references/concepts.md) — понятия: классификация, определение, деление.
- [`skills/logika/references/judgments.md`](skills/logika/references/judgments.md) — суждения: A/E/I/O, логический квадрат, распределённость, непосредственные умозаключения.
- [`skills/logika/references/syllogism.md`](skills/logika/references/syllogism.md) — силлогизм: фигуры и модусы, сведение, условные/разделительные, энтимемы и сориты.
- [`skills/logika/references/induction.md`](skills/logika/references/induction.md) — индукция: методы Милля, гипотеза, аналогия, классификация.
- [`skills/logika/references/errors.md`](skills/logika/references/errors.md) — каталог логических ошибок, софизмы и паралогизмы.
- [`skills/logika/references/laws.md`](skills/logika/references/laws.md) — четыре закона мышления.

**Docs**

- [`skills/logika/docs/konspekt.md`](skills/logika/docs/konspekt.md) — постатейный конспект всех 26 глав учебника Челпанова: суть, ключевые понятия, приёмы с современными примерами, чек-листы.

**Why it matters**

Embedding a structured logical reasoning skill allows the agent to go beyond heuristic pattern matching and produce traceable, rule-based arguments. This improves reliability for tasks that require precise logical validation, such as reviewing argumentative texts, educational tutoring, formal debate assistance, or error-checking of analytical writing.

## Install

This skill is distributed through the **rpa-skills** catalog (a Claude Code plugin marketplace), and also installs as a plain **skill folder** (Cursor, OpenAI Codex, Kimi Code CLI, and others).

**As a plugin (Claude Code)** — add the catalog once, then install this skill from it:

```text
/plugin marketplace add EvilFreelancer/rpa-skills
/plugin install logika@rpa-skills
```

**In Coddy**: the rpa-skills catalog is built into [Coddy](https://coddy.dev) as a system source,
so there is nothing to connect. One sync installs this skill together with the rest of the collection
into `~/.coddy/skills/logika/` and keeps it up to date (or press **Sync all** in Settings → Skills):

```bash
coddy skills sync
```

**As a plain skill folder** — copy the repository's `skills/logika/` directory into the tool's skills root. That directory contains the canonical `SKILL.md` and its `references/` and `docs/` files; preserve the directory name `logika`:

| Tool          | Path                          |
|---------------|-------------------------------|
| Coddy         | `~/.coddy/skills/logika/`       |
| Claude Code   | `~/.claude/skills/logika/`      |
| Cursor        | `~/.cursor/skills/logika/`      |
| OpenAI Codex  | `~/.agents/skills/logika/`      |
| Kimi Code CLI | `~/.kimi/skills/logika/`        |

For a manual installation, copy `skills/logika/` itself, not the repository root. The skill directory name must match the `name` field in `skills/logika/SKILL.md`.

Current Codex documentation uses `~/.agents/skills/` for user skills and `.agents/skills/` for repository skills. Install from GitHub with `$skill-installer`, or copy the complete `skills/logika/` directory into the chosen skills root. Some existing Codex setups use `~/.codex/skills/`; if that is the skills root your installation scans, use it instead. See [Codex skill installation and discovery](https://learn.chatgpt.com/docs/build-skills?product=breeze).

The repository uses the standard plugin layout `skills/logika/SKILL.md`. Codex's plugin guide places each skill in its own directory under `skills/` and points the manifest at that directory. Claude Code also scans `skills/` by default; it additionally permits a root-level `SKILL.md` for a one-skill plugin. That exception is valid, but the `skills/` layout keeps Logika's references inside the skill folder and works across the plugin formats used here. See the [Codex skill layout](https://developers.openai.com/plugins/build/skills), [Codex manifest field](https://developers.openai.com/plugins/deploy/submission), and [Claude Code plugin layout](https://code.claude.com/docs/en/plugins-reference#standard-layout).

## How to invoke

- **Slash command** — type `/logika` in agent chat; with the plugin installed, `/logika:review` runs the analysis-only mode.
- **`@` context** — attach the skill folder or `SKILL.md` to ground the message in these instructions.
- **Automatic** — the agent may load the skill on its own when your request matches the `description` in `SKILL.md`.

## Source & attribution

Part of **[rpa-skills](https://github.com/EvilFreelancer/rpa-skills)** — [Pavel Rykov](https://t.me/evilfreelancer)'s agent-skills collection (see [notes on vibe coding](https://t.me/evilfreelancer/1485) and the prompt collection [cursor-vibe-prompts](https://github.com/EvilFreelancer/cursor-vibe-prompts)).

Reference material is distilled from **G. Chelpanov's** classical formal-logic textbook «Учебник логики» (public domain). The full text of the textbook is not included in this repository.

Licensed under the MIT License — see [LICENSE](LICENSE).
