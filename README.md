# AI Study Camp's Claude Code Modules

Welcome to the AI Study Camp hands-on learning experience! This repo will teach you the core building blocks of Claude Code through 7 interactive modules — each one teaches a concept and gives you something to do.

## Prerequisites

- **Claude Code** installed on your computer ([install guide](https://docs.anthropic.com/en/docs/claude-code/overview))
- Basic comfort with opening a terminal
- Curiosity and willingness to experiment

## Getting Started

1. **Clone this repo**
   ```
   git clone https://github.com/aistudycamp/aisc-cc-modules.git
   ```

2. **Open the folder in your terminal**
   ```
   cd aisc-cc-modules
   ```

3. **Start Claude Code**
   ```
   claude
   ```

4. **Say hello!**
   Claude will greet you and guide you from there. No need to memorize anything — just follow along.

## Pausing and Resuming

Each module ends with a git commit that saves your progress — the checklist in `CLAUDE.md` tracks which modules you've completed. **Natural stopping points are between modules**, so if you need a break, try to wrap up the current module first.

If you need to stop mid-module, just close your terminal. When you come back, start Claude Code again with `claude` — it will see your checklist and guide you to pick up where you left off. The module in progress will simply restart.

**Pro tip:** If you want to resume the exact conversation you were in, run `claude --resume` instead of `claude`. This restores your previous session so you don't have to re-explain anything.

## What You'll Learn

| Module | Topic | Time | You'll Produce |
|--------|-------|------|----------------|
| 1 | Intro Tips & Tricks for Using Claude Code | ~20 min | *(no artifact — a practice session on plan mode, slash commands, and session management)* |
| 2 | CLAUDE.md | ~10 min | An "About Me" section added to your project's `CLAUDE.md` file |
| 3 | Skills | ~30 min | A new skill file at `.claude/skills/<your-skill>/SKILL.md` that you wrote from scratch |
| 4 | Plugins | ~30 min | Two community plugins installed and chained to produce three app-redesign mockups in `student-output/` |
| 5 | MCP Servers | ~30 min | A written list of 5 external tools you'd want Claude connected to, plus ONE live MCP connection working in your setup |
| 6 | Parallel Agents & Custom Sub-Agents | ~30 min | A two-part research briefing from 2 parallel agents, plus a reusable custom sub-agent file in `.claude/agents/` |
| 7 | Project Architecture | ~10 min | A clear mental model for how to organize a Claude Code project, plus a Next.js-style scaffolding example you can reuse |

**Total course time: ~2.5 hours.** You don't need to do it all at once — most students spread it across 2–3 sessions.

## What You'll Walk Away With

By the end, you will have:
- A customized CLAUDE.md you wrote yourself
- A skill you created from scratch
- A plugin installed from the marketplace
- A real MCP connection to an external service
- Hands-on experience orchestrating subagents in parallel
- A project architecture plan for your own work

## Examples and Templates

The `examples/` folder has reference files you can lift into your own projects. Click any link to view it.

| Category | File | What it is |
|----------|------|-----------|
| CLAUDE.md | [`example-global-claude-md.md`](examples/example-global-claude-md.md) | Minimal starter for `~/.claude/CLAUDE.md` |
| CLAUDE.md | [`example-project-claude-md.md`](examples/example-project-claude-md.md) | Minimal starter for a project's root `CLAUDE.md` |
| CLAUDE.md | [`example-global-claude-md-remy.md`](examples/example-global-claude-md-remy.md) | Full real-world global CLAUDE.md (AI with Remy newsletter) |
| CLAUDE.md | [`example-karpathy-guidelines.md`](examples/example-karpathy-guidelines.md) | Karpathy-inspired coding rules — drop-in fragment to `@`-import |
| Skills & MCP | [`example-skill.md`](examples/example-skill.md) | Annotated SKILL.md showing the full anatomy (frontmatter, when-to-use, references, templates, quality bar) |
| Skills & MCP | [`example-mcp-setup.md`](examples/example-mcp-setup.md) | Walkthrough for connecting your first MCP server |
| Project structure | [`example-project-scaffolding.md`](examples/example-project-scaffolding.md) | Full project folder anatomy with `@`-imports for personal + project context |
| Workflow | [`example-build-cycle.md`](examples/example-build-cycle.md) | The Plan → Build → Review cycle, with beginner and advanced patterns for each phase |
| Personal context | [`example-about-me-interview.md`](examples/example-about-me-interview.md) | Interview template that produces an `about-me.md` for personal context |
| Personal context | [`example-my-company-interview.md`](examples/example-my-company-interview.md) | Interview template for `my-company.md` (goals, focus, decisions) |

## Need Help?

If you get stuck at any point, just ask Claude! That's what it's here for.
