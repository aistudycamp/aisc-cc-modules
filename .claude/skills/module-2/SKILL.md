---
name: module-2
description: "Module 2: Best Practices — Learn how to use Claude Code like a pro with plan mode, slash commands, and session management"
---

# Module 2: Best Practices

You are running an interactive lesson for an AI Study Camp student. Follow the Greet, Teach, Show, Exercise, Celebrate pattern below. Be a warm, encouraging coach throughout.

---

## Step 1: Greet

Welcome the student to Module 2:

> "Great work finishing Module 1! Now that you know how CLAUDE.md shapes Claude's behavior, let's make sure you know how to actually USE Claude Code like a pro. This module covers the practical tips and tricks that will make your experience so much smoother."

---

## Step 2: Teach

Explain the key best practices one by one, in plain language:

### Plan Mode

- Before you ask Claude to build something big, you can enter **plan mode**. This tells Claude: "Don't start coding yet — let's think this through first."
- In plan mode, Claude will research, ask questions, and write out a step-by-step plan before touching any code or files. This prevents wasted work and misunderstandings.
- Think of it like a blueprint before building a house. You wouldn't start laying bricks without knowing the design, right?
- You enter plan mode by typing `/plan` or by pressing **Shift+Tab** to toggle it on before sending a message.
- Once you approve the plan, Claude switches back to normal mode and starts executing.

### Commands

- You've already used commands — like `module-1` to start the first lesson! There are two kinds of commands in Claude Code:
  - **Built-in commands** start with `/` (a forward slash):
    - `/help` — see what commands are available
    - `/clear` — start a fresh conversation while staying in the same project. Your CLAUDE.md and memories still apply, but the conversation history resets. Great when things get cluttered or you want to switch topics.
    - `/compact` — condenses the current conversation to save context space. Use this when conversations get long and Claude starts losing track of earlier details.
  - **Skills** are invoked by typing their name (no slash needed). For example, `module-1` runs the Module 1 skill. You'll learn how to create your own skills in Module 3!

### Resuming a Session

- When you close Claude Code and come back later, you can **resume where you left off**.
- Just run `claude --resume` or `claude -r` in your terminal, and Claude will pick up the previous conversation with full context.
- This is perfect for multi-day projects. You don't have to re-explain what you were working on.
- If you want to start completely fresh instead, just run `claude` without the resume flag.

### Giving Good Instructions

- Claude works best when you're clear about what you want. A few tips:
  - **Be specific.** "Fix the login bug" is vague. "The login form doesn't validate email addresses — add validation" is much better.
  - **Give context.** Tell Claude what you're trying to accomplish and why, not just what to do.
  - **Break big tasks into steps.** Instead of "Build me a website," try "Let's plan what pages we need, then build the homepage first."
  - **Correct Claude when it's wrong.** If Claude misunderstands, just say so. It learns from your feedback in the conversation.

### Keyboard Shortcuts

- **Escape** — cancel Claude's current response if it's going in the wrong direction. You don't have to wait for it to finish.
- **Shift+Tab** — toggle plan mode on/off before sending a message.
- These save a lot of time once you get used to them.

---

## Step 3: Show

Demonstrate these concepts interactively:

1. **Show /help:** Run the `/help` command or explain what it would show. Walk through the list of available commands so the student sees the full menu of options.

2. **Explain /clear in context:** "See how we've been having this long conversation across multiple modules? If you ever feel like things are getting cluttered or you want a clean slate, `/clear` resets the conversation. But here's the key: your CLAUDE.md instructions and your progress checklist are still there. It's like clearing your desk but keeping your filing cabinet."

3. **Explain resume:** "When we're done today and you close this terminal, you can come back tomorrow and type `claude --resume` to pick up right where we left off. No need to re-explain anything."

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

> "You now know how to use Claude Code like someone who's been using it for months! Plan mode, slash commands, session management, and giving good instructions — these are the habits that separate beginners from power users. And you just learned them in Module 2."

Then do these two things:

1. **Update the progress checklist** in CLAUDE.md by changing `- [ ] Module 2: Best Practices` to `- [x] Module 2: Best Practices`

2. **Direct them to the next module:**
   > "In Module 3, you'll learn about Skills — reusable instructions you can give Claude for specific tasks. You'll even build one yourself! Type `module-3` whenever you're ready!"
