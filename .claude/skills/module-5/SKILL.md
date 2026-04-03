---
name: module-5
description: "Module 5: Hooks — Understand automatic behaviors triggered by events in Claude Code"
---

# Module 5: Hooks

You are running an interactive lesson for an AI Study Camp student. Follow the Greet, Teach, Show, Exercise, Celebrate pattern below. Be a warm, encouraging coach throughout.

---

## Step 1: Greet

Welcome the student to Module 5:

> "Welcome to Module 5! You've already learned how to shape Claude's behavior with CLAUDE.md, picked up best practices, created reusable skills, and installed plugins. Now we're going to learn about something that takes things to the next level: Hooks -- automatic behaviors that run without you having to do anything. Let's dig in!"

---

## Step 2: Teach

Explain hooks using the "automatic rules" analogy:

- You know how you can set up rules on your phone or email? Things like: "When I get an email from my boss, move it to the Priority inbox" or "When I arrive at the gym, start playing my workout playlist." You set the rule once, and it runs automatically every time the trigger happens. Hooks work exactly the same way in Claude Code.
- A hook has two parts:
  - **The event** (the trigger) -- something that happens during a Claude Code session, like a tool being used, a session starting, or a notification firing
  - **The command** (the action) -- a shell script or command that runs automatically when that event occurs
- Hooks are configured in a JSON settings file (not a markdown file like skills). They use a structured format where you specify what event to watch for and what command to run.
- Here are the main event types you should know about:
  - **PreToolUse** -- fires BEFORE Claude uses a tool (like editing a file). Great for preventing mistakes or adding safety checks.
  - **PostToolUse** -- fires AFTER Claude uses a tool. Great for cleaning up, formatting, or running tests.
  - **SessionStart** -- fires when a new Claude Code session begins. Great for showing reminders or setting things up.
  - **Notification** -- fires when Claude sends a notification. Great for logging or routing alerts.
- Hooks are powerful because they work silently in the background. You don't have to remember to run them -- they just happen.

Point the student to `concepts/what-are-hooks.md` if they want to read more after the lesson.

---

## Step 3: Show

Read the example hook configuration file at `examples/example-hook-config.json` using your Read tool. Then walk through every piece clearly:

1. **The overall structure:** "This is a JSON file that defines hooks. Inside the `hooks` object, you see `PreToolUse` -- that's the event type. It means this hook runs BEFORE a tool is used."

2. **The matcher:** "See `\"matcher\": \"Edit|Write\"`? This narrows down WHICH tools trigger the hook. The pipe symbol `|` means 'or' -- so this hook fires before either the Edit tool or the Write tool runs. If Claude is about to edit or write a file, this hook kicks in."

3. **The command:** "This is the action that runs automatically. Let's break it down in plain language: it checks whether the file Claude is about to edit contains `.env` in the name. If it does, it prints a warning message: 'CAUTION: About to edit an environment file containing secrets!'"

4. **The exit code:** "See `exit 2` at the end? That's a special signal. In hooks, different exit codes mean different things:
   - Exit code 0 means 'everything is fine, continue'
   - Exit code 1 means 'something went wrong' (could block the action)
   - Exit code 2 means 'warn the user but let them decide whether to continue'
   So this hook doesn't block the edit -- it just makes sure you know what's happening before it proceeds."

5. **The description:** "This human-readable description helps you remember what the hook does when you look at your settings later: 'Warns before editing .env files that might contain secrets.' Always write clear descriptions for your hooks!"

6. **The big picture:** "So putting it all together: every time Claude is about to edit or write a file, this hook checks if it's a `.env` file. If it is, you get a warning. It's like having a safety guard watching over your sensitive files 24/7."

---

## Step 4: Exercise

This is a comprehension exercise, not a creation exercise. Hooks involve shell scripting, which is more advanced, so the goal here is understanding, not building.

Present the student with three scenarios and ask them to figure out which hook event type would be the right fit:

> "I'm going to describe three situations. For each one, tell me which hook event type you'd use. Don't worry about getting the exact syntax -- I just want to see if the concept clicks. Here we go:"

**Scenario 1:** "You want to automatically format code every time Claude edits a file. Which event type would you use?"
- Wait for their answer.
- **Answer:** PostToolUse (on the Edit tool). Explain: "You'd use PostToolUse because you want the formatting to happen AFTER Claude edits the file, not before. And you'd set the matcher to `Edit` so it only triggers on file edits."

**Scenario 2:** "You want a friendly reminder message to appear at the start of every Claude Code session -- something like 'Remember to check your task list!'"
- Wait for their answer.
- **Answer:** SessionStart. Explain: "SessionStart fires once when a new session begins. It's perfect for reminders, setup tasks, or displaying a welcome message."

**Scenario 3:** "You want to prevent Claude from accidentally deleting your test files when running terminal commands."
- Wait for their answer.
- **Answer:** PreToolUse (on the Bash tool). Explain: "You'd use PreToolUse because you want to check BEFORE the command runs. The matcher would be `Bash` since terminal commands go through the Bash tool. The hook could inspect the command and block it if it includes something like `rm` on your test directory."

After going through all three, reinforce the key takeaway:

> "The important thing is understanding the pattern: pick the right event (before, after, or on session start), set a matcher to narrow it down to the right tool, and define what should happen. When you're ready to create your own hooks, Claude can help you write the JSON and the shell commands -- you don't have to memorize the syntax."

**Success criteria:** The student correctly identifies at least 2 of the 3 event types. If they get all 3, extra celebration! If they struggle, walk through the reasoning patiently and make sure they understand before moving on.

---

## Step 5: Celebrate + Advance

Celebrate their understanding of this powerful feature:

> "You now understand one of Claude Code's most powerful features! Hooks are what separate casual users from power users. Even though we didn't build one today, you understand the concept -- and that's the hard part. When you're ready to create your own hooks, you can describe what you want in plain English and Claude will help you set it up."

Then do these two things:

1. **Update the progress checklist** in CLAUDE.md by changing `- [ ] Module 5: Hooks` to `- [x] Module 5: Hooks`

2. **Direct them to the next module:**
   > "You're over halfway through the course! Module 6 is about MCP Servers -- how Claude connects to external services like databases, APIs, and other tools. Type `/module-6` when you're ready to keep going!"
