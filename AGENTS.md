# Authoring & maintaining the `logika` skill

Agent guide for working **inside this skill repository**. Read it before editing `SKILL.md`, the README,
or any plugin manifest.

> Naming (Russian): the adjective for "agent / agentic" is **«агентный»**, never «агентский».

## Repository layout

This skill is packaged for **Claude Code**, **Cursor**, and **OpenAI Codex** (and installs as a plain
skill folder for Kimi Code CLI and others).

```
logika/
├─ .claude-plugin/
│  ├─ plugin.json        # Claude Code plugin manifest
│  └─ marketplace.json   # single-plugin marketplace (plugin lives at "./")
├─ .cursor-plugin/
│  └─ plugin.json        # Cursor plugin manifest
├─ .codex-plugin/
│  └─ plugin.json        # Codex plugin manifest (interface block + skills: "./skills/")
├─ skills/logika/
│  ├─ SKILL.md           # CANONICAL skill: YAML frontmatter + instructions
│  └─ references/ | scripts/   # optional bundled assets, next to SKILL.md
├─ SKILL.md              # COPY of skills/logika/SKILL.md (display / direct-copy install)
├─ README.md             # human overview
├─ AGENTS.md             # this file
└─ LICENSE
```

## ⚠️ Golden rule: a change anywhere must be synced across the whole skill

The same facts (the skill text, its `version`, its `description`) are duplicated in several files so the
skill works across platforms. **Whenever you edit one, propagate the change to every place it is mirrored —
in the same commit.** Nothing here is allowed to drift.

### 1. `SKILL.md` lives in two places — keep them byte-identical

- `skills/logika/SKILL.md` — **canonical**. What the Claude Code / Codex plugin loaders read, and what you
  copy when installing into `~/.claude/skills/logika/`, `~/.cursor/skills/logika/`, etc.
- `SKILL.md` (repo root) — a **copy** for GitHub display and direct-copy installs.

Edit the canonical file first, then sync the root copy and verify (the `diff` must print nothing):

```bash
cp skills/logika/SKILL.md SKILL.md
diff skills/logika/SKILL.md SKILL.md
```

Bundled assets (`references/`, `scripts/`, …) live **only** under `skills/logika/`, next to the canonical
`SKILL.md`, and are referenced from it by relative path. Do **not** duplicate them at the repo root.

### 2. `version` must match in every manifest

When you bump the version, update it in **all** of these:

- `skills/logika/SKILL.md` frontmatter — and the root `SKILL.md` copy.
- `.claude-plugin/plugin.json`
- `.claude-plugin/marketplace.json` (the entry inside `plugins`)
- `.cursor-plugin/plugin.json`
- `.codex-plugin/plugin.json`

### 3. `description` must stay consistent across manifests

The same description text appears in `SKILL.md` (root + canonical), `.claude-plugin/plugin.json`,
`.claude-plugin/marketplace.json`, `.cursor-plugin/plugin.json`, and `.codex-plugin/plugin.json`
(plus a shorter `interface.shortDescription` in the Codex manifest). Keep them in step.

Quick check that the version is identical everywhere:

```bash
grep -RhoE '"version"\s*:\s*"[^"]+"' .claude-plugin .cursor-plugin .codex-plugin | sort -u
```

## `SKILL.md` frontmatter

```yaml
---
name: logika
version: <semver>          # major.minor.patch
description: >
  When to use this skill and the triggers that should load it. Be specific — the agent uses this text
  to auto-select the skill.
---
```

- `name` **must** equal the directory name `logika` and the slash command (`/logika`).
- Bump `version` on every substantive change.

## README.md

Human-facing overview: purpose, when to use, usage examples, install (plugin + folder), and a
**Source & attribution** section. Keep it in step with `SKILL.md`.

## If the skill ships code

Put scripts under `skills/logika/scripts/`. Add tests where it makes sense and make sure they pass before
committing.

## Commit checklist

- [ ] `skills/logika/SKILL.md` edited where needed.
- [ ] Root `SKILL.md` synced — `diff skills/logika/SKILL.md SKILL.md` is clean.
- [ ] `version` bumped and identical in `SKILL.md`, `.claude-plugin/{plugin,marketplace}.json`,
      `.cursor-plugin/plugin.json`, `.codex-plugin/plugin.json`.
- [ ] `description` consistent across all manifests (and `interface.shortDescription` in Codex).
- [ ] README updated.
- [ ] Conventional commit message, e.g. `feat(logika): …` / `fix(logika): …`.

---

Part of the **[rpa-skills](https://github.com/EvilFreelancer/rpa-skills)** collection — see its `AGENTS.md`
for the collection-wide authoring process, and [cursor-vibe-prompts](https://github.com/EvilFreelancer/cursor-vibe-prompts).
