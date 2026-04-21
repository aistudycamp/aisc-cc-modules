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

## Need Help?

If you get stuck at any point, just ask Claude! That's what it's here for.
