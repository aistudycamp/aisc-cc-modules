# CLAUDE.md

## What is it?

Think of CLAUDE.md as a **briefing document you hand someone before they start a job**. When you hire a new assistant, you might give them a one-pager that says: "Here's how we work, here's what matters, here's what to watch out for." That's exactly what CLAUDE.md does for Claude.

It's a plain-text file that lives in the root of your project folder. Every time Claude starts a conversation in that project, it reads this file first -- before you even say anything. It shapes how Claude behaves, what it knows about your work, and what rules it should follow.

## Why does it matter?

Without a CLAUDE.md, Claude starts every conversation as a blank slate. With one, Claude already understands your preferences, your project structure, and your expectations -- so you spend less time repeating yourself and more time getting useful output.

## How does it work?

- You create a file called `CLAUDE.md` in your project's root folder
- Claude reads it automatically at the start of every session
- You write instructions in plain English -- no special syntax required
- You can update it anytime to change Claude's behavior

## Real-world examples

- **Set a writing style:** "Always write in a friendly, conversational tone. Avoid jargon."
- **Describe your project:** "This is a marketing site for a bakery. The audience is local customers aged 25-55."
- **Establish rules:** "Never delete files without asking me first. Always explain your reasoning."
- **Share context:** "We use Notion for project management and Google Docs for drafts. Our brand colors are navy and gold."
