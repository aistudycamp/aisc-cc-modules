<!-- Save this file to the root of your project as CLAUDE.md. It travels with the repo via git, so teammates get it too. -->

# Project CLAUDE.md

> The briefing every teammate (and Claude) reads when they open this repo. Keep it focused — the most important context goes first.

## Project Overview

- **What this is:** [One-sentence description of what this project does.]
- **Who it's for:** [Audience — internal users, customers, a specific team.]
- **Why it exists:** [The problem it solves or the goal it serves.]

## Tech Stack

- **Language(s):**
- **Framework(s):**
- **Database:**
- **Hosting / deploy target:**
- **Key external services:** [APIs, third-party tools the project depends on.]

## Folder Conventions

- `src/` — [what lives here]
- `tests/` — [what lives here]
- `docs/` — [what lives here]
- `.claude/` — Claude Code config: skills, agents, settings.
- *(Add or remove rows so this matches your real folder layout.)*

## Coding Standards

- **Style:** [Linter/formatter the project uses, e.g. Prettier + ESLint, ruff, gofmt.]
- **Tests:** [Testing framework and where tests live.]
- **Naming:** [Any naming conventions — kebab-case files, PascalCase components, etc.]
- **Comments:** [When to comment, when not to.]

## Commands & Scripts

- **Install dependencies:** `[command]`
- **Run dev server:** `[command]`
- **Run tests:** `[command]`
- **Lint / typecheck:** `[command]`
- **Build for production:** `[command]`

## About the Team

- **How we communicate:** [Slack, Discord, async-only, etc.]
- **How we ship:** [PR workflow, branch naming, review expectations.]
- **Glossary:** [Project-specific terms, acronyms, internal product names.]

## Things to Always Do

- Run tests before declaring work done.
- Update docs when behavior changes.
- Add `.env` values to `.env.example` (without secrets) when you add new env vars.

## Things to Never Do

- Never commit `.env`, secrets, or API keys.
- Never push to `main` without a reviewed PR.
- Never delete files without confirming first.

---

*Update this file as the project evolves. A stale CLAUDE.md is worse than no CLAUDE.md.*
