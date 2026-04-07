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

## Quick check

You need Claude to research three competing products and write a comparison. Would you do this with one Claude working sequentially, or with subagents? Why?

*(Subagents are the way to go here! Each subagent researches one product in parallel, then the main Claude combines the findings into a comparison. Faster, cleaner, and each subagent can focus deeply on its assigned product.)*
