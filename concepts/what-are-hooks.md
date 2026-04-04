# Hooks

## What is it?

You know how you can set up automatic rules on your phone? "When I arrive at work, turn on Wi-Fi." "When it's 9 AM, turn on Do Not Disturb." You set the rule once, and it runs automatically every time — no thinking, no deciding. Hooks work exactly the same way in Claude Code.

A hook is an **automatic rule that always does the exact same thing every time it fires.** The key difference from everything else you've learned: **hooks run outside of Claude's thinking entirely — no AI involved.** Claude doesn't decide whether to run them or how to run them. They just fire when the trigger event happens, silently in the background.

## Why does it matter?

Hooks remove manual steps from your workflow. Instead of remembering to check, format, or verify things yourself, hooks handle it automatically -- reducing mistakes and saving time. And they use zero context — they don't take up any of Claude's attention or memory.

## How does it work?

Each hook has two parts:
- A **trigger** (the event) — something that happens during a Claude Code session
- A **command** (the action) — what runs automatically when the trigger fires

Hooks are configured in a settings file. Don't worry about the exact format — the important thing is understanding the pattern. Here's an example:

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write",
        "hooks": [
          {
            "type": "command",
            "command": "npx prettier --write"
          }
        ]
      }
    ]
  }
}
```

Let's read it in plain English: "**After** (`PostToolUse`) Claude uses the **Write** tool (creates a file), automatically **clean up the formatting**." That's it — an event and an action. The `matcher` narrows it down to only fire for a specific tool, so it doesn't run on *everything*.

Available triggers include:
- **Before a tool runs** — great for safety checks ("warn me before editing sensitive files")
- **After a tool runs** — great for cleanup ("format code after every edit")
- **When a session starts** — great for reminders ("show my task list")
- **When a notification fires** — great for logging or routing alerts

## Real-world examples

- **Auto-format code:** Automatically clean up formatting every time Claude writes a file
- **Block sensitive edits:** Prevent Claude from modifying important files like `.env` (files that store passwords and secrets)
- **Run tests after changes:** Automatically run your test suite whenever Claude modifies code
- **Log activity:** Keep a record of what tools Claude used during a session for review later

## Quick check

You want a reminder to appear every time you start a new Claude Code session — something like "Remember to check your task list!" Which trigger would you use: before a tool runs, after a tool runs, or when a session starts?

*(If you said "when a session starts" — you've got it! That trigger fires once at the beginning of every conversation.)*
