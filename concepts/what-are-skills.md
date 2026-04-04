# Skills

## What is it?

You've been telling Claude "use a friendly tone, keep it under 300 words, include a call to action" every time you ask it to write a blog post. What if you could save those instructions once and reuse them forever?

That's what skills are. Think of them as **recipe cards** for Claude. Each one has step-by-step instructions for a specific task. Instead of re-explaining yourself, you just tell Claude which recipe card to grab.

There are two kinds:
- **Action skills** — workflows you trigger by name, like pulling out a recipe card. ("Hey Claude, run `write-blog-post`.")
- **Reference skills** — knowledge Claude draws on automatically when relevant, like a style guide sitting on the shelf. You don't invoke them — Claude just reaches for them when they're useful.

## Why does it matter?

Skills let you get consistent, repeatable results without re-explaining yourself. Once you've dialed in a great workflow for a task, you save it as a skill and reuse it forever.

## What does one look like?

Here's a simple skill that runs a daily standup:

```yaml
---
name: daily-standup
description: Asks three standup questions and formats a summary.
---
```
```markdown
Ask the user these three questions, one at a time:
1. What did you accomplish yesterday?
2. What are you working on today?
3. Any blockers?

Then format the answers into a clean summary.
```

The part between the `---` lines is the label on the recipe card (its name and what it does). Everything below is the recipe itself — plain English instructions that Claude follows. You'd run this one by typing `daily-standup`.

## How does it work?

- Skills are stored as text files inside a `.claude/skills/` folder in your project — each skill gets its own folder with a file called `SKILL.md`
- **Action skills** are invoked by typing their name (like `write-blog-post`). Claude reads the instructions and follows them.
- **Reference skills** load automatically when Claude decides they're relevant to what you're working on -- you don't need to invoke them.
- You can set a skill to only load when you invoke it manually, keeping Claude's attention focused.

## Real-world examples

- **Writing blog posts:** A skill that defines your brand voice, target word count, formatting rules, and SEO checklist
- **Analyzing survey data:** A skill that tells Claude how to summarize responses, flag trends, and format a report
- **Generating social media captions:** A skill that specifies platform, tone, hashtag strategy, and character limits
- **Creating meeting agendas:** A skill that pulls in attendees, topics, and time blocks in your preferred format

## Quick check

You want Claude to always follow the same 5-step process when helping you write a newsletter. Would you use an action skill or a reference skill? And what would you name it?

*(If you said "an action skill, maybe called `write-newsletter`" — you nailed it! Action skills are for workflows you trigger on demand.)*
