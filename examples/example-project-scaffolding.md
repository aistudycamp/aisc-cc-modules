<!-- A walkthrough of a typical Claude Code project layout, with a sample CLAUDE.md that pulls in personal context, project docs, and behavioral rules via @-imports. -->

# Project Scaffolding: How a Real Claude Code Project Hangs Together

> The minimal template at `example-project-claude-md.md` shows the *what*. This file shows the *how*: a working folder layout, plus a CLAUDE.md that ties together your personal context, project docs, and behavioral rules.

---

## The folder layout

Here's what a real Claude Code project tends to look like once you've wired it up:

```
my-project/
├── CLAUDE.md                       # Project briefing. Loaded by Claude every session.
├── CLAUDE.local.md                 # Personal overrides. Gitignored — your sticky notes on the shared rules.
├── .env                            # Secrets (API keys, DB URLs). NEVER commit.
├── .env.example                    # Safe template listing which env vars exist. Committed.
├── .gitignore
├── .claude/
│   ├── skills/                     # Project skills (committed; shared with the team).
│   ├── agents/                     # Custom sub-agents (committed).
│   └── settings.local.json         # Personal Claude Code settings. Gitignored.
├── concepts/                       # Reference docs Claude reads on demand.
├── docs/                           # Human-facing docs (architecture, ADRs, glossary).
├── src/                            # Your actual code.
└── README.md
```

The split that matters:

- **Shared** (committed to git): `CLAUDE.md`, `.claude/skills/`, `.claude/agents/`, `concepts/`, `docs/`, `src/`, `README.md`
- **Personal** (gitignored, yours alone): `CLAUDE.local.md`, `.claude/settings.local.json`, `.env`

Every teammate gets the shared set when they clone. Each person arranges their own desk however they like.

---

## A sample project CLAUDE.md with @-imports

This is the kind of CLAUDE.md you'd actually keep at your project root. The `@` lines pull in other files at session start so Claude has the right context without you copy-pasting it everywhere.

```markdown
# My Project

> A [one-sentence description] for [audience]. The goal is [outcome].

## Personal context (from my home folder)

@~/.claude/ABOUT-ME/about-me.md
@~/.claude/ABOUT-ME/my-company.md
@~/.claude/ABOUT-ME/anti-ai-writing-style.md

## Project context (from this repo)

@docs/architecture.md
@docs/conventions.md
@concepts/glossary.md

## Behavioral rules

@.claude/karpathy-guidelines.md

## Project Overview

- **What this is:** [one-sentence description]
- **Tech stack:** [language, framework, key services]
- **Folder conventions:** [where things live]

## Things to always do

- Run tests before declaring work done.
- Update docs when behavior changes.

## Things to never do

- Never commit `.env`.
- Never push to main without a reviewed PR.
```

---

## How @-references resolve

Three path styles, three different scopes:

| Path style | What it means | Example | Use when |
|-----------|--------------|---------|----------|
| `@~/path/to/file.md` | Home-relative — anywhere on your machine | `@~/.claude/ABOUT-ME/about-me.md` | Pulling in *personal* context that should travel with you, not the repo (about-me, anti-ai-writing-style, my-company). |
| `@path/to/file.md` | Project-relative — resolved from CLAUDE.md's location | `@docs/architecture.md` | Pulling in repo-internal docs, conventions, glossaries — anything teammates also need. |
| `@/absolute/path/file.md` | Absolute path | `@/Users/me/shared/style.md` | Rare. Use when a file lives outside both home and the project (a shared mount, a synced folder). |

A few practical notes:

- **Imports run on every session start**, alongside CLAUDE.md itself. Updates to the imported files take effect on the next conversation.
- **Imports compose**: an imported file can `@`-import other files. Keep the chain shallow so Claude isn't loading half your hard drive.
- **Broken paths fail silently**. If a teammate doesn't have `~/.claude/ABOUT-ME/`, the import is just skipped, no error. Handy for personal-context lines that only resolve on your machine — but verify with a session start if you're depending on it.

---

## Common patterns

- **Inline vs `@`-import:** if a rule is short and project-specific (5-10 lines), inline it. If it's a doc that gets reused across projects (about-me, anti-ai-writing-style, behavioral guidelines), `@`-import it.
- **Personal context goes home, project context goes in the repo.** A teammate cloning the repo shouldn't pull in *your* about-me, which is why personal files live under `~/.claude/` and get imported by path rather than committed.
- **Behavioral rules can travel as fragments.** Drop `example-karpathy-guidelines.md` into your project root (or `~/.claude/`) and `@`-import it from any CLAUDE.md. One file, many projects.
- **Read-on-every-turn rules go at the top.** The first thing in CLAUDE.md should be the most important context. Claude scans top-down, so imports that load critical files belong above optional sections.

---

*Treat this file as a starting point. Copy the parts that fit your project into your own CLAUDE.md, prune the rest.*
