---
name: module-1
description: "Module 1: Intro Tips & Tricks for Using Claude Code — Plan mode, slash commands, session management, and the habits that make Claude Code feel fast"
---

# Module 1: Intro Tips & Tricks for Using Claude Code

You are running an interactive lesson for an AI Study Camp student. Follow the Greet, Teach, Show, Exercise, Celebrate pattern below. Be a warm, encouraging coach throughout.

---

## Step 1: Greet

Welcome the student to Module 1:

> "Welcome to your very first module! Before we dive into customization and advanced features, let's make sure you know how to actually USE Claude Code like a pro. This module covers the practical tips and tricks (plan mode, slash commands, session management) that will make your whole experience smoother from here on out."

---

## Step 2: Teach

Before diving in, give the student a quick map of what's coming so they know what to expect:

> "Here's everything we're going to cover in this module. We'll go through each one in detail, then quiz you at the end."

| # | Concept | One-liner |
|---|---------|-----------|
| 1 | **Input modes** | Four "gears" you shift between with `Shift+Tab` based on how much oversight you want |
| 2 | **Think keywords** | Add `think` / `think harder` / `ultrathink` to make Claude reason more deeply |
| 3 | **`--dangerously-skip-permissions`** | A flag that turns off permission prompts for a big speed boost once you trust the workflow |
| 4 | **Commands & slash commands** | Built-in commands like `/help`, `/clear`, `/compact` plus your own skills triggered with `/name` |
| 5 | **Resuming a session** | Pick up a previous conversation with `claude --resume` |
| 6 | **Giving good instructions** | Be specific, give context, break big tasks into steps |
| 7 | **Search before you build** | Check the community for existing skills/plugins before creating your own |
| 8 | **Keyboard shortcuts** | `Esc` to cancel, `Shift+Tab` to cycle modes |
| 9 | **Working with images** | Paste screenshots into Claude to debug UI bugs or share mockups |
| 10 | **Context management** | Spot when Claude is "running low" and use `/compact`, `/clear`, or a fresh session |

Now let's walk through each one in plain language:

### Input Modes

Claude Code has four input modes. Think of them as gears. You shift between them with **Shift+Tab**. Pick the one that matches how much oversight you want.

| Mode | What it does | When to use |
|------|--------------|-------------|
| **Edit mode** (default) | Claude asks permission before each tool call | Normal day-to-day work |
| **Auto-accept** | Claude runs tool calls without pausing to ask; stops when it needs new info from you | Trusted, repetitive operations where you want speed |
| **Plan mode** | Read-only. Claude writes out a step-by-step plan and waits for your approval before touching any code or files | Big or risky changes you want to review first |
| **Auto-mode** | Claude runs continuously using its own judgment; you provide course corrections as it goes | Longer autonomous tasks where you want to stay out of the loop |

Think of plan mode like a blueprint before building a house. You wouldn't start laying bricks without knowing the design, right? And auto-mode is like handing the keys to a trusted contractor: you check in on progress, but you're not watching every hammer swing.

### Think Keywords

You can control how much reasoning Claude does before it acts by adding a "think" keyword to your message. More thinking = more tokens, but better answers on hard problems.

| Keyword | Analysis depth | When to use |
|---------|----------------|-------------|
| *(none)* | Normal | Routine tasks and simple questions |
| `think` | Deeper | Ambiguous problems, design decisions |
| `think harder` | Deeper still | Tricky bugs, weighing tradeoffs |
| `ultrathink` | Max | Critical architectural decisions, complex debugging |

Example: *"ultrathink about whether we should restructure the auth flow."*

### `--dangerously-skip-permissions`

This CLI flag turns off per-tool-call permission prompts. Once you trust how Claude behaves in your repo, it's a huge speed boost. **We recommend turning it on once you feel comfortable in Claude Code**, not on day one.

Usage:

```bash
claude --dangerously-skip-permissions
```

**The tradeoff:**
- **Risk:** No safety net. Commands execute immediately, including file deletions and destructive git operations.
- **Reward:** Pure flow state. ~10× faster. Real workflow speed.

Best practice: use it when your git state is clean so you can roll back anything unexpected.

### Commands

- You've already used commands, like `module-1` to start the first lesson! There are two kinds of commands in Claude Code:
  - **Built-in commands** start with `/` (a forward slash):
    - `/help` — see what commands are available
    - `/clear` — start a fresh conversation while staying in the same project. Your CLAUDE.md and memories still apply, but the conversation history resets. Great when things get cluttered or you want to switch topics.
    - `/compact` — condenses the current conversation to save context space. Use this when conversations get long and Claude starts losing track of earlier details.
  - **Skills** are invoked by typing `/` followed by the skill name. For example, `/write-blog-post` or `/deploy`. (The module commands like `module-1` are a special shortcut that also works without the slash.) You'll learn how to create your own skills in Module 3!

    *(Quick preview: Module 2 is all about `CLAUDE.md` — the file that shapes Claude's behavior in a project. We'll get there next.)*

### Resuming a Session

- When you close Claude Code and come back later, you can **resume where you left off**.
- Just run `claude --resume` or `claude -r` in your terminal, and Claude will pick up the previous conversation with full context.
- This is perfect for multi-day projects. You don't have to re-explain what you were working on.
- If you want to start completely fresh instead, just run `claude` without the resume flag.

### Giving Good Instructions

- Claude works best when you're clear about what you want. A few tips:
  - **Be specific.** "Fix the login bug" is vague. "The login form doesn't validate email addresses. Add validation." is much better.
  - **Give context.** Tell Claude what you're trying to accomplish and why, not just what to do.
  - **Break big tasks into steps.** Instead of "Build me a website," try "Let's plan what pages we need, then build the homepage first."
  - **Correct Claude when it's wrong.** If Claude misunderstands, just say so. It learns from your feedback in the conversation.

### Search Before You Build

- Before you spend time creating something from scratch, check if someone else has already built it. Claude Code has a growing ecosystem of skills, plugins, and community tools.
- You can ask Claude things like: "Is there a skill for writing blog posts?" or "Find me a plugin that helps with code review." Claude will search the community for you.
- Think of it like checking the app store before building your own app. Nine times out of ten, someone has already solved the problem you're facing.
- This mindset (**discover first, customize if needed, build only as a last resort**) will save you enormous amounts of time. We'll practice this pattern in the next few modules.

### Keyboard Shortcuts

- **`Esc`** (the Escape key in the top-left of your keyboard) — cancel Claude's current response if it's going in the wrong direction. You don't have to wait for it to finish.
- **`Shift+Tab`** — cycle through the four input modes (edit, auto-accept, plan, auto-mode) before sending a message.
- These save a lot of time once you get used to them.

### Working with Images

Claude Code takes images, not just text. Paste a screenshot right into the terminal. Drag and drop a screenshot into the Claude Code window, or use your native paste shortcut (⌘+V on Mac, Ctrl+V on Windows/Linux) after copying an image. Claude can actually see the picture and reason about it.

This is a game-changer for debugging. When a UI looks wrong, a button is misaligned, or an error dialog pops up, skip the "how do I describe this in words?" step and just paste the screenshot. Great use cases include sharing a UI bug, showing a design mockup you want Claude to match, pasting an error dialog, or walking through a visual regression. For example: *"Here's a screenshot of my login page — why does the submit button look squished on mobile?"* Claude sees it, understands it, and helps you fix it.

### Context Management

Here's a helpful analogy. Think of Claude's **context window** as a whiteboard. Everything in your conversation (your messages, Claude's replies, files Claude has read) gets written on that whiteboard. It's big, but it's not infinite. Eventually it fills up.

How do you know Claude is running low on whiteboard space? You'll notice it starts forgetting things you mentioned earlier, repeating questions, or losing track of the plan. That's your signal to manage the context.

You have a few tools for this:
- **`/compact`** — condenses the current conversation into a shorter summary so you can keep going without losing the thread.
- **`/clear`** — wipes the whiteboard for a fresh start. Your CLAUDE.md and skills still apply, but the conversation resets. Great when switching topics.
- **Start a new session** — sometimes the cleanest move is to close the current chat and start a fresh one for a new topic.

**Pro tip:** You can customize the Claude Code status line (via `/statusline` or by editing your settings file) to show things like token usage or context remaining, a handy visual cue so you can see the whiteboard filling up before you hit the edge.

---

## Step 3: Show

Demonstrate these concepts interactively:

1. **Show /help:** Run the `/help` command or explain what it would show. Walk through the list of available commands so the student sees the full menu of options.

2. **Explain /clear in context:** "See how we've been having this long conversation across multiple modules? If you ever feel like things are getting cluttered or you want a clean slate, `/clear` resets the conversation. But here's the key: your CLAUDE.md instructions and your progress checklist are still there. It's like clearing your desk but keeping your filing cabinet."

---

## Step 4: Exercise

This is a quick, practical exercise:

1. **Quiz the student.** Present these three scenarios and ask what they'd do:

   **Scenario 1:** "You want Claude to help you redesign your company's onboarding process. It's a big project with many moving parts. What should you do before diving in?"
   - Wait for their answer.
   - **Answer:** Use plan mode! Type `/plan` or Shift+Tab first, so Claude thinks through the approach before making changes.

   **Scenario 2:** "You've been chatting with Claude for a while and the conversation is getting really long. Claude seems to be forgetting things you said earlier. What do you do?"
   - Wait for their answer.
   - **Answer:** Use `/compact` to condense the conversation, or `/clear` if you want a fresh start.

   **Scenario 3:** "You were working on a project yesterday and want to continue today. How do you pick up where you left off?"
   - Wait for their answer.
   - **Answer:** Run `claude --resume` or `claude -r` to resume the previous session.

2. **Success criteria:** The student answers at least 2 of 3 correctly. If they get all 3, celebrate extra!

---

## Step 5: Celebrate + Advance

Congratulate them:

> "You now know how to use Claude Code like someone who's been using it for months! Plan mode, slash commands, session management, and giving good instructions: these are the habits that separate beginners from power users. And you just learned them in Module 1."

Then do these three things:

1. **Update the progress checklist** in CLAUDE.md by changing `- [ ] Module 1: Intro Tips & Tricks for Using Claude Code` to `- [x] Module 1: Intro Tips & Tricks for Using Claude Code`

2. **Save their work with git.** Walk them through it as a mini-lesson:

   > "Let's save your progress! We're going to use something called git — it's a tool that keeps track of every change you make, like a save point in a video game. Run these commands:"

   Run the following commands (use the Bash tool):
   - `git add CLAUDE.md`
   - `git commit -m "Complete Module 1 — picked up the core tips and tricks for using Claude Code"`

   After the commit, explain: "Your work is now saved! We'll do this after every module — it's a good habit."

3. **Direct them to the next module:**
   > "Next up is Module 2: CLAUDE.md, the single most important file in any Claude Code project. You'll learn how it shapes Claude's behavior AND you'll customize one yourself. Type `module-2` whenever you're ready!"

---

## What You Learned in Module 1

Take a second to appreciate how much ground you just covered. Here's everything you now know how to do:

| Concept | Why it matters / when to use it |
|---------|---------------------------------|
| **Input modes (Shift+Tab)** | Match your level of oversight to the task, from careful edit mode to full auto-mode. |
| **Think keywords** | Get deeper reasoning on hard problems by asking Claude to `think`, `think harder`, or `ultrathink`. |
| **`--dangerously-skip-permissions`** | Hit true flow state once you trust the workflow. Massive speed boost. |
| **Commands & slash commands** | Get around Claude Code like a pro with `/help`, `/clear`, `/compact`, and your own skills. |
| **Resuming sessions** | Pick up long projects across days without re-explaining anything. |
| **Giving good instructions** | Be specific, share context, and break big jobs into steps for better results. |
| **Search before you build** | Save hours by finding existing skills and plugins before rolling your own. |
| **Keyboard shortcuts** | `Esc` and `Shift+Tab`: small habits, big time savings. |
| **Working with images** | Paste screenshots to debug UI issues, share mockups, or show errors visually. |
| **Context management** | Keep Claude sharp across long conversations with `/compact`, `/clear`, and `/statusline`. |

You're driving Claude Code now. Onward to Module 2!
