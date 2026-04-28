<!-- A more robust example skill, showing the full anatomy: clear when-to-use guards, structured steps, lazy-load references, templates, a quality bar, and tone. Save this content as .claude/skills/<skill-name>/SKILL.md to install it in a project. -->

---
name: daily-standup
description: Run a quick daily standup — asks three questions and formats a summary.
---

# Daily Standup

Help the user run a quick daily standup check-in.

## When to use

- The user says "let's do a standup," "daily check-in," "what should I work on today," or similar.
- Auto-invokes when the request matches the description above (Claude reads the description on every turn and routes accordingly).

## When NOT to use

- For weekly retrospectives — different format, longer horizon.
- For status updates to a manager — those want outcomes, not WIP.

## Steps

1. **Ask the three standup questions, one at a time.** Wait for each answer before moving on:
   - "What did you work on yesterday (or last session)?"
   - "What are you planning to work on today?"
   - "Is anything blocking your progress?"

2. **For framing tips on each question** (what counts as a real blocker, how to phrase yesterday's work, etc.), see `references/standup-cheatsheet.md`. Only read it if an answer is vague and you need to coach the user.

3. **Format the result** using the template at `templates/standup-format.md`. Fill in the user's three answers and stamp today's date at the top.

4. **Quality bar before declaring done:**
   - Each answer is concrete (a task or outcome, not "stuff").
   - Blockers name a person or decision needed, not "I'm stuck."
   - The summary is short enough to paste into Slack without editing.

## Tone

Casual and encouraging. This is a quick check-in, not a formal report. If an answer is vague, ask one follow-up — don't grill.
