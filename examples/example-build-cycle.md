<!-- A walkthrough of the end-to-end Claude Code build cycle: Plan → Build → Review. Each phase has a "Start here" mode for beginners and a "Going deeper" mode for once Claude Code feels natural. Lift any patterns into your own CLAUDE.md. -->

# The Build Cycle: Plan → Build → Review

> How a real Claude Code session moves from idea to shipped code. Three phases, each with a beginner pattern and a more advanced one. Start with the simple version. Level up when those feel automatic.

---

## How power users work

Plan → Build → Review is the working pattern of practitioners who ship a lot with Claude Code. Boris Cherny (who built Claude Code at Anthropic) and Garry Tan (Y Combinator) have both shared their workflows publicly, and the through-line is the same: spend more time planning than feels natural, build with verification baked in, and treat review as a parallel-agent job rather than a single-pass checklist.

This guide is that pattern, distilled. Use it to give yourself concrete tools for each phase so you stop wondering "what should I be doing right now?"

---

## How to use this guide

Each phase has two modes:

- **Start here** — the simplest version that gets you most of the value. Just two tools per phase. If you're new to Claude Code, read these and skip the rest.
- **Going deeper** — once Start here feels automatic, layer in subagents, plugins, and parallel patterns. Don't rush this; the simple version is doing more than you realize.

You don't have to use every phase every time. A bug fix might skip Plan. A refactor might skip Build. Use the cycle as a checklist; the exact order can flex.

---

## Phase 1: Plan

**You're in this phase when:** the path forward isn't obvious. You're not sure how to architect something, you have multiple competing approaches, or you're about to spend an hour writing code you might throw away.

**Why it matters:** the cost of a bad plan is hours of wasted code. The cost of a good plan is 5 extra minutes. Worth it nearly always.

### Start here

Two tools, both built in or one-click installable:

1. **Plan mode.** Press `Shift+Tab` until "Plan" shows in the input bar. Claude will write out a step-by-step plan and wait for your approval before touching any code or files.
2. **`/brainstorm` from the superpowers plugin.** Run `/install-plugin superpowers` once, then type `/brainstorm` whenever you want to explore options before committing to one direction, or say brainstorm in your prompt and it will be invoked.

These two together cover most planning needs.

**Especially great for:** UI/UX design (have Claude propose 3 design directions before you commit), architecture decisions (REST vs GraphQL, monolith vs services), and scoping conversations where you're tempted to just "start coding."

### Sample prompts

- "Enter plan mode and walk me through how you'd build [feature]."
- "Brainstorm 3 different approaches to [problem]. For each, name the biggest tradeoff."
- "Show me the smallest version that ships. What would I cut to ship it tomorrow?"
- "Walk me through how a senior engineer would approach this, without writing code yet."

### Going deeper

Once plan mode and `/brainstorm` feel natural, layer in:

- **The `/plan` skill** from superpowers, which runs a more structured planning workflow that produces a written plan document you can hand off to a fresh session.
- **Custom subagents for planning.** A `@planner` for breaking down work, an `@architect` for design tradeoffs, a `@user-researcher` for design feedback from the user's perspective. Dispatch them in parallel with one prompt: *"@planner outline the work, @architect flag risks, @user-researcher poke at the UX."*

---

## Phase 2: Build

**You're in this phase when:** the plan exists and it's time to make it real.

**Why it matters:** this is where most "Claude Code went off the rails" stories happen. The fix is verification baked into the workflow — Claude checking its own work before declaring done.

### Start here

Two practices, both wired into your CLAUDE.md:

1. **Tell Claude to verify.** Add to your CLAUDE.md: *"Verify your work before declaring it done. Run the tests. Check the output. Don't say 'should work.' Say 'I ran X and got Y.'"*
2. **Use `/clear` between tasks.** When you finish one feature and start another, `/clear` resets the conversation so old context doesn't pollute the new work. Your CLAUDE.md and skills still apply.

That's it for the simple version. Just two habits.

### Sample prompts to understand what Claude is doing

The dirty secret of LLM-assisted coding: half the value is in *understanding* what got built. Use these to keep your hand on the wheel:

- "Walk me through why you built it this way."
- "What tradeoffs did you make? What did you NOT do, and why?"
- "What would a senior engineer push back on?"
- "Show me the smallest change that would break this."
- "If I hand this to a teammate tomorrow, what's the first thing they'll be confused by?"

These work in any project. They're free. Use them.

### Going deeper

Once the basics feel solid, add:

- **`frontend-design` plugin** for production-quality UI mockups and pages. Run `/install-plugin frontend-design`.
- **WebSearch for library research.** Before installing a new dependency, ask: *"Search for the most active, well-maintained library for [task]. Compare the top 3 by recent commits, downloads, and open issues. Recommend one."*
- **Playwright MCP** for live browser QA during build. Claude can open a page, click around, and report what it sees — closing the loop between code and behavior.
- **Per-commit reports.** Add this rule to CLAUDE.md: *"After every `git commit`, write a one-paragraph summary to `.claude/reports/YYYY-MM-DD-<slug>.md` describing what changed, why, and what to verify next."* Add `.claude/reports/` to `.gitignore`. The folder becomes a personal log you can scan after a long session to catch anything you missed and decisions Claude made.
- **Custom subagents for build.** An `@engineer` for technical gut-checks ("is this overcomplicated?"), a `@designer` for visual feedback on a screenshot.

---

## Phase 3: Review

**You're in this phase when:** the code works locally and you're about to merge.

**Why it matters:** review is where bugs that would cost a week get caught for free. The trick is parallelism — run multiple reviewers at once, each with a focused lens, and the whole pass takes minutes.

### Start here

One prompt, no setup:

> "Review the diff between this branch and main. Flag bugs, security issues, and anything a code reviewer would call out. Be honest. Don't just say it looks good."

That's it. One Claude, one diff, one review. Catches the obvious stuff and most of the medium stuff.

### Going deeper

Build a review squad: multiple specialized subagents running in parallel, each with a different lens.

A typical squad:

- **`@code-reviewer`** — correctness, performance, code quality
- **`@security-reviewer`** — secrets, auth, injection, dependency risks
- **`@qa-tester`** — runs the tests, checks for regressions, exercises edge cases
- **`@ux-reviewer`** — visual QA on rendered pages (especially with Playwright MCP)

Dispatch them with one prompt:

> "@code-reviewer, @security-reviewer, @qa-tester, and @ux-reviewer in parallel — review the diff since main and report findings. Each agent: stay in your lane."

You get four expert reviews back in the time one would take. Each agent runs in its own context so they don't pollute each other.

**Sample prompts:**

- "Run the review squad on this branch."
- "@code-reviewer focus on the changes in `src/auth/`."
- "@qa-tester — write a test for the new edge case before declaring this done."

---

## Wiring it into CLAUDE.md

Drop this section into your project's CLAUDE.md to make the cycle automatic:

```markdown
## Workflow

### Plan first
- For any task with 3+ steps, design decisions, or unknowns, enter plan mode (Shift+Tab) before writing code.
- Use `/brainstorm` when there's no clear right answer.
- (Going deeper: dispatch @planner + @architect for big features.)

### Build with discipline
- Verify your work before declaring it done. Run the tests. Check the output. Don't say "should work." Say "I ran X and got Y."
- After every `git commit`, write a one-paragraph summary to `.claude/reports/YYYY-MM-DD-<slug>.md` describing what changed, why, and what to verify next.
- (Going deeper: invoke `frontend-design` for UI work; use Playwright MCP for live browser QA.)

### Review in parallel
- Before merging, ask for a code review. Simple version: "Review the diff against main."
- (Going deeper: dispatch @code-reviewer + @security-reviewer + @qa-tester + @ux-reviewer in parallel.)
```

And add to `.gitignore`:

```
.claude/reports/
```

---

*Treat this cycle as a starting frame. The exact tools matter less than the discipline of moving deliberately through Plan → Build → Review. Strip what doesn't fit your work; add what does.*
