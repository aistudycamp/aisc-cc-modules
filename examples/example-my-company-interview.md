<!-- An interview template that produces my-company.md (current goals, strategy, decisions). Paste the body into Claude Code and let it interview you. Run after about-me.md is set up. -->

# My-Company Interview Template

> A guided interview that produces a condensed `my-company.md` capturing current goals and strategic focus. Run after `about-me.md` is set up. Updates on a "when priorities change" cadence, not a schedule.
>
> **No overlap with `about-me.md`:** identity goes in about-me; goals and strategy go here.

---

You are building my `my-company.md` file for my Cowork folder. This file tells Claude what I'm working toward right now so it can make better decisions on every task.

Important: my `about-me.md` already covers who I am, how I work, and my standards. This file is ONLY about goals, strategy, and decisions. No overlap.

Your job: interview me using AskUserQuestion (6-8 questions), then compile the answers into a condensed `my-company.md` under 1,000 tokens.

## How to interview me

Use AskUserQuestion for every question. One question at a time. Let me use "Other" to dictate long answers when I need to.

## What to cover (6-8 questions)

**GOALS (3-4 questions)**
- What are your top 2-3 goals for this year? Specific numbers or milestones.
- What platforms, channels, or markets matter most right now?
- What's the one metric that would tell you this year was a success?
- Do you have revenue targets, audience targets, or product milestones? What are they?

**DECISIONS (3-4 questions)**
- What are you actively saying no to right now? (opportunities, trends, platforms, tactics)
- What did you recently stop doing? Why?
- Where are you spending most of your time and energy this quarter?
- Is there anything you're betting on that most people in your field aren't?

## Output format

After the interview, compile everything into a single markdown file. Short sections, mostly bullet points. No filler. No identity info (that's in `about-me.md`).

Structure:

````markdown
# MY COMPANY

## Goals
[Bullet points. Specific targets with numbers where possible. Organized by category if needed.]

## Focus right now
[What I'm spending time and energy on this quarter. 2-3 bullet points max.]

## Saying no to
[Bullet points. Things I'm actively declining or ignoring.]
````

Target: under 1,000 tokens. Update this file when priorities change, not on a schedule.

Save the file as `my-company.md` in your `ABOUT ME/` folder.
