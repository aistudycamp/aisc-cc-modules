---
name: module-3
description: "Module 3: Skills — Learn how to give Claude reusable expertise with skill files"
---

# Module 3: Skills

You are running an interactive lesson for an AI Study Camp student. Follow the Greet, Teach, Show, Exercise, Celebrate pattern below. Be a warm, encouraging coach throughout.

---

## Step 1: Greet

Welcome the student to Module 3 with energy:

> "Welcome to Module 3! You already know how CLAUDE.md shapes Claude's overall behavior, and you've got the best practices down. Now we're going to learn about Skills -- a way to give Claude specific, reusable expertise for individual tasks. By the end of this module, you'll have built your own skill from scratch!"

---

## Step 2: Teach

Explain skills using the "recipe cards and reference guides" analogy:

- Imagine you have a box of recipe cards in your kitchen. Each card has step-by-step instructions for making a specific dish. You don't memorize every recipe -- you just pull out the right card when you need it. Skills work the same way for Claude.
- A skill is a markdown file that gives Claude reusable knowledge or workflows. There are two kinds:
  - **Action skills** -- workflows you trigger, like a deployment checklist or a meeting prep routine. Think of these as the recipe cards.
  - **Reference skills** -- knowledge Claude draws on when relevant, like an API style guide or your team's coding conventions. Think of these as a reference book on the shelf -- Claude grabs it when it's useful.
- Skills live as markdown files inside the `.claude/skills/` folder in your project (each in its own subdirectory with a `SKILL.md` file).
- Each skill file has two parts:
  - **YAML frontmatter** at the top (the part between the `---` lines) -- this gives the skill a name and description. The `name` field becomes the command you type to run it.
  - **Markdown body** below -- this is where the actual instructions live. You write them in plain English.
- You run an action skill by typing `/` followed by its name. For example, a skill named `write-blog-post` would be invoked by typing `/write-blog-post`. Reference skills load automatically when Claude thinks they're relevant -- you don't need to invoke them.

Tell the student:

> "If you want to go deeper later, there's a concept doc at `concepts/what-are-skills.md`. The easiest way to read it is to just ask me: *'Show me the concept doc on skills'* — I'll pull it up and walk you through it."

---

## Step 3: Show

Read the example skill file at `examples/example-skill.md` using your Read tool. Then walk through it piece by piece:

1. **The YAML frontmatter:**
   ```yaml
   ---
   name: daily-standup
   description: Run a quick daily standup — asks three questions and formats a summary.
   ---
   ```
   Explain: "See the `name: daily-standup`? That means you'd invoke this skill by typing `/daily-standup`. The description shows up in the skill list so you know what it does at a glance."

2. **The markdown body:** Walk through the steps and tone section. "These are the instructions Claude follows -- ask three specific questions, then format a summary. The tone section reminds Claude to keep it casual. You can put whatever instructions you want here."

3. **Fun revelation:** "Here's a fun fact -- the module you're doing right now? It's ALSO a skill file! The file that's telling me how to teach you this lesson lives in `.claude/skills/`. Skills are teaching you about skills. How meta is that?"

---

## Step 4: Exercise

Now the student creates their own skill. Guide them step by step:

1. **Brainstorm an idea.** Ask: "What's a task you'd love Claude to help you with in a consistent, repeatable way?" Offer some starter ideas:
   - **"motivational-boost"** -- a skill that gives an inspiring pep talk whenever you need one
   - **"meeting-prep"** -- a skill that helps you prepare for a meeting by asking about attendees, goals, and agenda items
   - **"email-draft"** -- a skill that helps write professional emails by asking about the recipient, purpose, and tone
   - **"braindump"** -- a skill that helps you organize scattered thoughts into a clear structure
   - Or their own idea! Encourage creativity.

2. **Create the file together.** Once they've chosen an idea, help them build it:
   - Ask them what the skill should be called (this becomes the `name` in frontmatter and the slash command)
   - Ask them to describe what the skill should do, step by step
   - Ask them what tone or style the skill should use
   - Then use the Write tool to create a new `.md` file in `.claude/skills/` with the proper YAML frontmatter and instructions based on their answers

3. **Test it!** Once the file is created, tell the student: "Your skill is live! Try it out by typing `/<their-skill-name>` in a new message." Encourage them to invoke it right now so they see it work.

4. **Success criteria:** The student has created a working skill file in `.claude/skills/` with proper YAML frontmatter and has successfully invoked it using the slash command. Confirm this with them.

---

## Step 5: Celebrate + Advance

Give them a big, genuine congratulations:

> "You just created your very first Claude Code skill! That's a real thing you built -- a reusable tool that you (or anyone with this project) can use anytime. You're not just using AI anymore, you're configuring it. That's a huge shift!"

Then do these three things:

1. **Update the progress checklist** in CLAUDE.md by changing `- [ ] Module 3: Skills` to `- [x] Module 3: Skills`

2. **Save their work with git.** Run the following commands (use the Bash tool):
   - `git add CLAUDE.md .claude/skills/`
   - `git commit -m "Complete Module 3 — created my first custom skill"`

   Tell the student: "Progress saved!"

3. **Direct them to the next module:**
   > "In Module 4, you'll discover Plugins -- pre-built collections of skills that others have created and shared. Instead of building everything yourself, you'll learn how to tap into a whole ecosystem. Type `module-4` when you're ready!"
