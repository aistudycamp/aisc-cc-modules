<!-- An interview template that walks you through producing your own about-me.md. Paste the body into Claude Code (or a Cowork session) and let it interview you. -->

# About-Me Interview Template

> A guided interview prompt that produces a condensed `about-me.md` for use with Claude. Paste the body into Claude Code and let it interview you. Output goes in your `ABOUT ME/about-me.md` (or wherever you keep personal context).

---

## How to interview me

Use AskUserQuestion for every question. One question at a time. Let me use "Other" to dictate long answers when I need to.

If I give a vague answer, push back. Ask for a specific example or rephrase. Don't accept "I like to keep things clear" without knowing what clear looks like in my work.

Follow interesting threads. If something unexpected comes up, go deeper before moving on.

## What to cover (15-20 questions, adapt based on what matters for my role)

**WHO I AM (3 questions)**
- What do I do? What's my role, my company, my industry?
- Who do I work with or work for? (clients, team, stakeholders, audience)
- What does a good week of work look like for me?

**HOW I WORK (4 questions)**
- What tools do I use every day and how?
- Walk me through how I start a typical task from zero to done.
- What does my review/editing/QA process look like?
- When I hand something off (to a client, a boss, a reader), what does "done" look like?

**WHAT GOOD LOOKS LIKE (4 questions)**
- Show me or describe the best output you've produced recently. What made it good?
- What separates great work from average work in your field?
- When you look at someone else's work and think "this is good," what are you reacting to?
- If I had to judge your work, what should I be looking for?

**WHAT YOU HATE (4 questions)**
- What's an example of bad work in your field? What specifically makes it bad?
- What patterns, shortcuts, or habits in your industry make you cringe?
- When Claude writes something for you and it's wrong, what's usually off? (tone, structure, detail level, assumptions)

**YOUR RULES (3 questions)**
- What do you never do in your work? Hard lines you won't cross.
- What are the 2-3 non-negotiables that every piece of your work must have?

**YOUR OPINIONS (3 questions)**
- What do you believe about your field that most of your peers would push back on?
- What tools, methods, or trends do you think are overrated? What's underrated?

## Output format

After the interview, compile everything into a single markdown file. Do NOT save raw Q&A transcripts. Extract the patterns from my answers and write them as condensed prose and bullet points.

Structure:

````markdown
# ABOUT ME: [My Name]

## Who I am
[2-3 sentences. My role, my work, my audience/clients. Current facts and numbers if relevant.]

---

## How I work
[My daily tools, my process, how I start tasks, how I review, what "done" looks like. Short paragraphs.]

---

## What good looks like
[What I value in my own work and others'. The standards I hold. Condensed from examples I gave.]

---

## What I hate
[Patterns, shortcuts, and mistakes that bother me. What "wrong" looks like. Specific, not vague.]

---

## My rules
[Numbered list. Hard lines and non-negotiables.]

---

## Instructions for Claude
[10 numbered rules for how to work with me. Derived from everything above. Focus on what Claude must DO and NOT DO, not abstract principles.]
````

Target: under 2,000 tokens total. Every sentence should carry signal. If a sentence could be cut without losing information, cut it.

Save the file as `about-me.md` in your `ABOUT ME/` folder.

---

**Tip:** Dictate your answers when you need to say specific things. Use Wispr Flow (free, faster than typing).
