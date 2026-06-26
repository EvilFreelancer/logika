# Logika (formal logic)

**Purpose**: Provides the agent with a classical formal‑logic framework based on G.Chelpanov’s textbook. It enables the
model to perform rigorous logical analysis, construct and evaluate syllogisms, detect logical fallacies, and apply
inductive reasoning methods.

**When to use**

- Analyzing arguments or checking the validity of inferences.
- Classifying concepts, judgments, or logical forms.
- Building or reducing syllogisms, proving statements, or identifying logical errors.
- Applying the laws of thought (identity, non‑contradiction, excluded middle, sufficient reason).
- Performing inductive reasoning using Mill’s methods, analogies, or hypothesis generation.

**Core workflow**

1. Identify the logical objects involved (concepts, judgments, inferences, proofs).
2. Load the appropriate reference files from `references/` (e.g., `concepts.md`, `syllogism.md`).
3. Verify each step against the relevant logical rules.
4. Produce a clear conclusion: validity, detected fallacy, or the correct inference.

**Reference files**

- `references/concepts.md` – definitions and classification of terms.
- `references/judgments.md` – square of opposition, immediate inferences.
- `references/syllogism.md` – syllogistic figures, moods, reduction techniques.
- `references/induction.md` – Mill’s methods, analogical reasoning.
- `references/errors.md` – catalogue of logical fallacies.
- `references/laws.md` – fundamental laws of thought.

**Why it matters**

Embedding a structured logical reasoning skill allows the agent to go beyond heuristic pattern matching and produce
traceable, rule‑based arguments. This improves reliability for tasks that require precise logical validation, such as
educational tutoring, formal debate assistance, or error‑checking of argumentative text.

## Install

This skill is packaged as a plugin for **Claude Code**, **Cursor**, and **OpenAI Codex**, and also installs as a plain **skill folder** (Kimi Code CLI and others).

**As a plugin (Claude Code):**

```text
/plugin marketplace add EvilFreelancer/logika
/plugin install logika@logika
```

**As a plain skill folder** — copy or symlink `skills/logika/` into a skill root:

| Tool          | Path                          |
|---------------|-------------------------------|
| Claude Code   | `~/.claude/skills/logika/`      |
| Cursor        | `~/.cursor/skills/logika/`      |
| OpenAI Codex  | `~/.codex/skills/logika/`       |
| Kimi Code CLI | `~/.kimi/skills/logika/`        |

The directory name must match the `name` field in `SKILL.md`.

## How to invoke

- **Slash command** — type `/logika` in agent chat.
- **`@` context** — attach the skill folder or `SKILL.md` to ground the message in these instructions.
- **Automatic** — the agent may load the skill on its own when your request matches the `description` in `SKILL.md`.

## Source & attribution

Part of **[rpa-skills](https://github.com/EvilFreelancer/rpa-skills)** — [Pavel Zloi](https://t.me/evilfreelancer)'s agent-skills collection (see [notes on vibe coding](https://t.me/evilfreelancer/1485) and the prompt collection [cursor-vibe-prompts](https://github.com/EvilFreelancer/cursor-vibe-prompts)).

Reference material is distilled from **G. Chelpanov's** classical formal-logic textbook (concepts, judgments, syllogisms, induction, fallacies).

Licensed under the MIT License — see [LICENSE](LICENSE).
