# Glossary

Key terms you'll encounter in the AI Study Camp, in plain language.

---

**CLAUDE.md** -- A configuration file that gives Claude instructions, context, and rules for your project. Think of it as a briefing document Claude reads before every conversation.

**CLAUDE.local.md** -- A personal override file for CLAUDE.md that only applies to you. It lives in the project root but is gitignored, so your personal preferences aren't shared with teammates.

**CLI (Command Line Interface)** -- A text-based way to interact with your computer by typing commands instead of clicking buttons. Claude Code runs in the CLI.

**Clone** -- Making a copy of a project (repository) from the internet onto your own computer so you can work with it locally.

**Context window** -- The total amount of text Claude can "see" in a single conversation, including your messages, Claude's replies, and any files it reads. When the window fills up, older content gets summarized to make room — key decisions and code are preserved.

**Hook** -- An automatic action that runs when a specific event happens, like formatting code every time a file is saved. Configured in your project settings.

**MCP (Model Context Protocol)** -- A standard that lets Claude connect to external tools and services (like email, calendars, or browsers) through small adapter programs called servers.

**Memory** -- Information Claude saves between sessions so it can remember your preferences, past decisions, and project context without you repeating yourself.

**Plan Mode** -- A mode in Claude Code where Claude explores and plans without making changes. You enter it by typing `/plan` or pressing Shift+Tab. Great for thinking through an approach before writing code.

**Plugin** -- A pre-built package of skills and configurations you can install to give Claude new capabilities, similar to installing an app on your phone.

**Project Architecture** -- How you organize your Claude Code configuration files — CLAUDE.md, skills, hooks, settings — within a project folder so everything works together and is easy to maintain.

**Prompt** -- The text you type to tell Claude what you want it to do. A good prompt is clear, specific, and includes relevant context.

**Repository (Repo)** -- A project folder that lives on a platform like GitHub. It contains all your files plus a built-in "undo history" that tracks every change anyone has ever made — so you can always go back to an earlier version.

**Skill** -- A saved set of instructions that tells Claude how to perform a specific task, like writing a blog post or analyzing data. Invoked with a slash command.

**Slash command** -- A shortcut that starts with `/` (like `/write-blog-post`) used to trigger a skill or built-in action in Claude Code.

**Subagent** -- A second Claude that the first one sends off to handle a specific job, like a manager asking a teammate to look into something while they keep working on the main task.

**Token** -- The smallest unit of text Claude processes. For example, the word "hamburger" is 3 tokens, and the sentence "I love cats" is 3 tokens. Tokens determine how much fits in the context window and how usage is measured — think of them as the "units" Claude counts in.
