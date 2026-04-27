# CLAUDE.md

## What is it?

Have you ever had to explain the same thing to someone every single morning? Your preferences, your project, what happened yesterday — all from scratch? That's what working with AI usually feels like. Every conversation starts from zero.

CLAUDE.md fixes that. It's a simple file you create in your project folder — think of it as a **briefing document you hand someone before they start a job.** "Here's who we are, here's how we work, here's what matters." Claude reads it before every conversation, so you never have to repeat yourself.

You write it in plain English (no special format or coding required), and you can open it in any text editor. One file, and Claude shows up already knowing how to help you.

## Why does it matter?

Without a CLAUDE.md, Claude starts every conversation as a blank slate. With one, Claude already understands your preferences, your project structure, and your expectations -- so you spend less time repeating yourself and more time getting useful output.

## Where CLAUDE.md lives

CLAUDE.md isn't just one file — it lives at multiple scopes, and they stack on top of each other.

The two you'll use most:

- **Global** — `~/.claude/CLAUDE.md` in your home directory. Personal preferences, workflow defaults, communication style. Applies to *every* project you open on this machine.
- **Project** — `CLAUDE.md` in the root folder of a repo. Project-specific context, team conventions, what this codebase is for. Committed to git so teammates get it automatically when they clone.

A simple way to decide where something goes: if you'd want Claude to follow this instruction *no matter what project you're in*, it's global. If it's about *this specific project or team*, it's project-level.

Two more advanced scopes exist — directory-level (e.g. `frontend/CLAUDE.md` for rules that only apply inside that folder) and personal overrides (`CLAUDE.local.md`, gitignored, for rules you don't want to share with the team). Module 7 covers those in depth — don't worry about them yet.

## How does it work?

- You create a file called `CLAUDE.md` in your project's root folder (the main folder for your project), or in `~/.claude/` for the global version
- Every time you start a new conversation, Claude reads this file first — before you even say anything
- You write instructions in plain English -- no special syntax required
- You can update it anytime, and Claude's behavior changes immediately in the next conversation

## Real-world examples

- **Set a writing style:** "Always write in a friendly, conversational tone. Avoid jargon."
- **Describe your project:** "This is a marketing site for a bakery. The audience is local customers aged 25-55."
- **Establish rules:** "Never delete files without asking me first. Always explain your reasoning."
- **Share context:** "We use Notion for project management and Google Docs for drafts. Our brand colors are navy and gold."

## Quick check

Imagine you're building a project for a client who is very particular about formal language — no contractions, no slang, always professional. Where would you put that instruction so Claude follows it in every conversation? And what might it look like?

*(If you answered "in CLAUDE.md, something like: Always use formal language — no contractions or slang" — you've got it!)*
