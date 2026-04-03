# Hooks

## What is it?

Hooks are like **automatic rules you set on your phone**: "When I arrive at work, turn on Wi-Fi" or "When it's 9 AM, turn on Do Not Disturb." You define the trigger and the action once, and it runs automatically every time.

In Claude Code, hooks are automatic actions that fire when specific events happen during your session. You don't have to remember to run them -- they just happen in the background.

## Why does it matter?

Hooks remove manual steps from your workflow. Instead of remembering to check, format, or verify things yourself, hooks handle it automatically -- reducing mistakes and saving time.

## How does it work?

- Hooks are configured in your project's `settings.json` file using a simple JSON format
- Each hook has a **trigger** (the event) and a **command** (what to run)
- Available triggers include: before/after a tool runs, when a session starts, and when a notification fires
- The command runs automatically whenever the trigger event occurs

Example of what a hook looks like in your settings:
```json
{
  "hooks": {
    "afterToolUse": [
      { "command": "npm run format", "match_tool": "write" }
    ]
  }
}
```

## Real-world examples

- **Auto-format code:** Automatically clean up formatting every time Claude writes a file
- **Block sensitive edits:** Prevent Claude from modifying important files like `.env` or credentials
- **Run tests after changes:** Automatically run your test suite whenever Claude modifies code
- **Log activity:** Keep a record of what tools Claude used during a session for review later
