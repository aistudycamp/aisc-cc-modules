# Subagents

## What is it?

Some tasks are too big for one conversation. Imagine you need to research three things at once, but Claude can only focus on one thing at a time. What if Claude could send out helpers to work on each one simultaneously?

That's what subagents are. Think of them as **teammates you can delegate to**. The main Claude is the manager — it identifies what needs to be done, then sends off separate Claudes to handle specific jobs independently. Each subagent works on its own, without seeing the main conversation or the other subagents. When they're done, they report back with their results, and the main Claude combines everything.

It's like a project lead saying: "You research competitor A, you research competitor B, and you research competitor C. Come back when you're done and I'll put together the final report."

## Why does it matter?

Subagents give you three big advantages:

- **Context isolation.** Each subagent works in its own space, so its research and notes don't clutter up your main conversation. Your chat stays clean and focused.
- **Parallel work.** Multiple subagents can work at the same time, instead of doing everything one after another. Three research tasks that would take three rounds? They all happen at once.
- **Specialized focus.** Each subagent gets one clear job and puts all its attention there. It's not trying to juggle — it's heads-down on its specific task.

When a subagent finishes, the main Claude gets back a summary of what it found — not every detail of its entire process. You get the results without the noise.

## How does it work?

Here's the basic pattern:

1. **The main Claude (the manager) decides to delegate.** It identifies tasks that can be handled independently.
2. **It creates one or more subagents,** each with a specific assignment — like "research this topic" or "review this file."
3. **Each subagent works independently.** It doesn't see the main conversation, and it doesn't see what the other subagents are doing. It just focuses on its job.
4. **Each subagent reports back** when it's done, returning its findings to the main Claude.
5. **The main Claude combines everything** and presents you with the final result.

You don't need to manage this process yourself — Claude handles the delegation and coordination behind the scenes. You just ask for what you need, and Claude decides when subagents would help.

## Real-world examples

- **Research multiple topics at once:** Ask Claude to compare three products, and it sends a subagent to research each one in parallel
- **Review code while writing docs:** One subagent reviews your code for issues while another drafts documentation — both at the same time
- **Analyze data from different sources:** Subagents each dig into a different dataset, then the main Claude synthesizes the findings
- **Audit a codebase from multiple angles:** One subagent checks for security issues, another looks at performance, another reviews code style — all simultaneously

## Custom sub-agents: a permanent specialized team

So far we've been talking about **ad-hoc agents** — temporary workers spun up for one specific task. There's a second flavor worth knowing: **custom sub-agents.** These are *permanent* AI team members you define once and reuse forever.

The difference in one line:

- **Ad-hoc agents** are for *doing* many things in parallel.
- **Custom sub-agents** are for getting *specialized perspectives* you need repeatedly.

### What makes a custom sub-agent

A custom sub-agent is just a markdown file in your project's `.claude/agents/` folder. Each one defines:

- A **name and emoji** (the emoji shows up in your terminal so you can see which specialist is talking)
- A **color** (visual distinction — purple, blue, green, red, etc.)
- A **persona** (background, communication style, what they care about)
- An **expertise** list (the specific skills they bring)

Once defined, you summon them by name. Instead of telling Claude "act like an engineer" every time, you build a real `👨‍💻 Engineer` sub-agent once — with 10 years of pretend experience, direct communication style, and architecture expertise — and call them whenever you need a technical gut-check.

### When to use which

| Scenario | Use this |
|----------|----------|
| Process 20 meeting notes simultaneously | Ad-hoc agents (parallel workers) |
| Get technical feedback on specs weekly | Custom sub-agent (Engineer) |
| Research 5 competitors at once | Ad-hoc agents (one-time) |
| Convert weekly updates into exec summaries | Custom sub-agent (Executive) |
| Analyze 50 user interviews in parallel | Ad-hoc agents (batch processing) |
| Get UX perspective on designs repeatedly | Custom sub-agent (User Researcher) |

Ad-hoc = many workers, one task. Custom = one specialist, called again and again.

### Anatomy of a sub-agent file

```markdown
# 👨‍💻 Engineer

## Color
purple

## Persona
You are an experienced software engineer with 10+ years at top tech
companies. Direct and pragmatic. Flag risks early; suggest alternatives
when something won't work.

## Expertise
- System architecture and design patterns
- Performance optimization and scalability
- Spotting edge cases and error states
```

Save that as `.claude/agents/engineer.md` and you've got a permanent Engineer on your team. Call them any time with `👨‍💻 Engineer, review @dashboard-prd.md`. Run `/agents` to list everyone you've hired.

## Quick check

You need Claude to research three competing products and write a comparison. Would you do this with ad-hoc agents or with a custom sub-agent? Why?

*(Ad-hoc agents are the way to go here! It's a one-time parallel task — three workers researching three products simultaneously. A custom sub-agent would make sense if you had to review products every week and wanted a "🔍 Product Analyst" you could call on repeatedly.)*
