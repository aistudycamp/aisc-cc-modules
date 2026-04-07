# Project Architecture

## What is it?

You've got a CLAUDE.md, some skills, a few hooks, maybe an MCP connection or two — but where does everything go? How do you keep it all organized so it actually works?

That's what project architecture is about. Think of it as a **well-organized office**. You wouldn't toss your contracts, reference books, and sticky notes into the same pile. You'd put contracts in the filing cabinet, reference books on the shelf, and daily reminders on the bulletin board. A Claude Code project works the same way — there are specific places where each type of configuration lives, and putting things in the right place means everything runs smoothly.

## Why does it matter?

A messy project means Claude might miss important instructions, skills might not load properly, and teammates might not know where to find things. Good architecture means everything just works — Claude picks up the right instructions, skills load when they should, and your setup is easy to understand and maintain.

## How does it work?

Here are the key locations in a Claude Code project and what goes where:

- **`CLAUDE.md`** (project root) — Your master instruction file. Claude reads this at the start of every conversation. It's the briefing document that sets the tone, rules, and context for the whole project.

- **`.claude/skills/`** — Where skills live. Each skill gets its own folder with a `SKILL.md` file inside it. This is the recipe book shelf.

- **`.claude/settings.local.json`** — Your personal settings: hooks, permissions, MCP connections. This file is gitignored, so it stays on your machine only.

- **`CLAUDE.local.md`** — Your personal overrides for CLAUDE.md. Maybe you want a different tone, or extra instructions just for you. Also gitignored — teammates never see it.

Here's an easy way to remember which files are shared and which are personal:

**Shared with your team** (committed to git):
- `CLAUDE.md` — project instructions everyone follows
- `.claude/skills/` — skills the whole team can use
- `concepts/` — reference docs and learning materials

**Personal only** (gitignored, stays on your machine):
- `.claude/settings.local.json` — your local settings
- `CLAUDE.local.md` — your personal instruction overrides

## Real-world examples

- **Marketing team:** The shared `CLAUDE.md` has brand voice rules, approved terminology, and formatting standards that everyone follows. Each team member has a personal `CLAUDE.local.md` with their own workflow preferences — one person likes bullet-point drafts, another prefers full paragraphs.
- **Dev team:** Shared skills for deployment and code review live in `.claude/skills/` so every developer has access. Each developer's `.claude/settings.local.json` has their own MCP connections to their individual development database.
- **Solo project:** Even working alone, separating shared files from personal ones is a good habit. When you eventually invite a collaborator, they can clone the repo and get all the shared setup immediately — without inheriting your personal quirks.

## Quick check

You're working on a team project. Where would you put instructions that only apply to you (not your teammates)?

*(CLAUDE.local.md is the answer! It's gitignored, so it stays on your machine. Your teammates get the shared CLAUDE.md, and you get your personal layer on top.)*
