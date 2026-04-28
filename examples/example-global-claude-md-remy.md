<!-- A more advanced, real-world example of a global CLAUDE.md. Save to ~/.claude/CLAUDE.md to apply globally across every project on your machine. Lift the patterns that fit your workflow; ignore the rest. Note it's generally recommended to keep CLAUDE.md files under 300 lines. -->

# Remy's Global CLAUDE.md

_Shared with AI with Remy newsletter readers on 2026-04-23._

This is the Claude Code instructions file that applies to all my projects and sessions. It lives at `~/.claude/CLAUDE.md` and gets loaded into every Claude Code session.

Sensitive details (personal identifiers, specific client names, private service paths) have been redacted. Workflow patterns, rules, and structure are unchanged. Copy what's useful, ignore what isn't.

---

# Global Claude Code Instructions

These instructions apply to all projects and sessions.

@~/Desktop/Vault/Areas/AI with Remy/_context/

---

## Workflow Orchestration

### 1. Plan Mode Default
- Enter plan mode for ANY non-trivial task (3+ steps or architectural decisions)
- If something goes sideways, STOP and re-plan immediately, don't keep pushing
- Use plan mode for verification steps, not just building
- Write detailed specs upfront to reduce ambiguity

### 2. Subagent & Agent Team Strategy

#### Default Posture: Delegate First
- **Always prefer subagents** over doing work directly in the main context window
- The main context is for orchestration, decision-making, and user communication, not grunt work
- If a task involves reading more than 2-3 files, searching broadly, or producing intermediate analysis, it belongs in a subagent

#### When to Spawn Subagents
- **Research & exploration**: Codebase search, reading docs, understanding architecture, investigating bugs
- **Implementation**: Writing code, editing files, running tests, especially in worktree isolation
- **Verification**: Running test suites, checking build output, validating changes
- **Any task that would consume >20% of the context window** with tool results or intermediate output

#### Subagents vs Agent Teams, Decision Framework

**Use regular subagents** when:
- Tasks are **sequential** (output of one feeds into the next), always subagents
- Tasks are **parallel but independent** (no need for agents to coordinate with each other), launch multiple subagents in a single message
- Tasks are **short/focused**, the overhead of standing up a team isn't worth it
- You need **results back in the main context** to make a decision before continuing

**Use Agent Teams mode** (`CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`) when:
- Tasks are **parallel AND agents need to coordinate** with each other (shared context, handoffs, feedback loops)
- The work benefits from **agent-to-agent discussion**, e.g. a researcher and writer iterating together without the lead relaying messages
- The task is **large enough** to justify the overhead of a shared task list and mailbox system
- You want agents to **self-organize** around a task list with dependency tracking

**Key distinction for parallel work:**
- Parallel + no coordination needed → **multiple subagents** (simpler, cheaper, results flow back to lead)
- Parallel + agents need to talk to each other → **Agent Teams** (mesh communication, shared task list)

Common parallel subagent patterns (no team needed):
- Multiple Explore agents searching different parts of the codebase
- Build + lint + test agents all verifying in parallel
- Research agent in background while continuing other work
- Use a single message with multiple Agent tool calls to launch parallel subagents

#### Context Window Hygiene
- **Never dump large file contents into the main context**, have a subagent read and summarize
- **Never run broad searches in the main context**, delegate to an Explore agent
- **Keep the main context for**: user communication, high-level planning, orchestrating agents, making decisions based on agent results
- If you catch yourself about to read a large file or run a broad search directly, STOP and delegate instead

#### Agent Type Selection
- `Explore`, codebase search, file discovery, architecture questions (read-only, fast)
- `Plan`, designing implementation strategy, identifying files to change, trade-off analysis
- `Bash`, git operations, running builds/tests, shell commands
- `general-purpose`, multi-step tasks combining search + analysis, complex research
- Use `isolation: "worktree"` for implementation agents that write code, to avoid conflicts

#### Resuming Agents
- Track agent IDs from completed tasks, resume them for follow-up work instead of spawning new ones
- Resuming preserves full context, avoiding re-explanation overhead

### 3. Verification Before Done
- Never mark a task complete without proving it works
- Diff your behavior between main and your changes when relevant
- Ask yourself: "Would a staff engineer approve this?"
- Run tests, check logs, demonstrate correctness

### 4. Demand Elegance (Balanced)
- For non-trivial changes: pause and ask "is there a more elegant way?"
- If a fix feels hacky: "Knowing everything I know now, implement the elegant solution"
- Skip this for simple, obvious fixes, don't over-engineer
- Challenge your own work before presenting it

### 5. Autonomous Bug Fixing
- When given a bug report: just fix it. Don't ask for hand-holding
- Point at logs, errors, failing tests, then resolve them
- Zero context switching required from the user
- Go fix failing CI tests without being told how

### 6. Boil the Ocean
- The marginal cost of completeness is near zero with AI. Do the whole thing. Do it right. Do it with tests. Do it with documentation. Do it so well that I'm genuinely impressed, not politely satisfied, actually impressed. Never offer to "table this for later" when the permanent solve is within reach. Never leave a dangling thread when tying it off takes five more minutes. Never present a workaround when the real fix exists.
- The standard isn't "good enough", it's "holy shit, that's done." Search before building. Test before shipping. Ship the complete thing. Time is not an excuse. Fatigue is not an excuse. Complexity is not an excuse. Boil the ocean.

### Core Principles
- **Simplicity First**: Make every change as simple as possible. Impact minimal code.
- **No Laziness**: Find root causes. No temporary fixes. Senior developer standards.
- **Minimal Impact**: Changes should only touch what's necessary. Avoid introducing bugs.
- **Batch file edits**: Plan all changes to a file upfront. Apply in one call (`MultiEdit` or `Write`), never sequential `Edit`s on the same file.

## Obsidian — Second Brain

Obsidian is the single source of truth for all project context, brand information, strategy docs, meeting notes, and business knowledge.

### Architecture
- **Vault path:** `~/Desktop/Vault`
- **Workspaces path:** `~/Desktop/OS`, where code projects live
- Obsidian provides the *context*. Workspaces are where the *work* happens. They work hand-in-hand.

### Vault Structure
```
Vault/
  Areas/                          (business areas / brands)
    [Brand 1]/         → Workspace: [brand-1]/
    [Brand 2]/         → Workspace: [brand-2]/
    Clients/
      [Client A]/      → Workspace: clients/[client-a]/
      [Client B]/      → Workspace: clients/[client-b]/
    Personal/          → Workspace: personal/
  Projects/                       (project management — all active/planned projects tracked here)
  Meeting Notes/
  Notes/
  Logs/
  _System/
```

### CLI Commands Reference
- Use the CLI via Bash: `obsidian <command>` (Obsidian must be running)
- Key commands:
  - `obsidian read file="Note Name"`, read a specific note
  - `obsidian search query="..." format=json`, search the vault
  - `obsidian search:context query="..."`, search with surrounding context
  - `obsidian daily:read`, today's daily note
  - `obsidian daily:append content="..."`, append to today's daily note
  - `obsidian tasks`, list all tasks
  - `obsidian tags`, list all tags
  - `obsidian properties file="..."`, read note properties/frontmatter
  - `obsidian backlinks file="..."`, find what links to a note
- Use `format=json` for structured output when parsing results programmatically.
- Behavioral rules (context loading, CLI vs QMD routing, workflow) are in `~/.claude/rules/obsidian.md`.

---

## Reserved Local Services

These services run permanently on my machine via macOS Launch Agents. **Never override, reassign, or conflict with these ports unless explicitly instructed.**

| Service | Address | Launch Agent | Data |
|---------|---------|-------------|------|
| [Redacted] | `http://localhost:[port]` | `com.[redacted].server` | `~/.[redacted]/instances/default/` |

To manage: `launchctl list | grep [service]` (check status), `launchctl stop com.[service].server` (stop), `launchctl start com.[service].server` (start).

## MCP Servers

- Global MCP server configs live in `~/.claude.json` under the `mcpServers` key.

## Vercel Deployment

- **Always remind the user** to manually link the GitHub repo to the Vercel project via the Vercel dashboard after creating a new project, CLI-created projects don't auto-deploy on push.

## Telegram Bot

- Global skill scripts at `~/.claude/skills/telegram-bot/`
- **Bot tokens are per-workspace**, each workspace has a `.claude/.telegram-env` file
- `TELEGRAM_ALLOWED_USER` (my user ID, redacted) is global in `~/.zshrc`
- Scripts auto-load `.claude/.telegram-env` from the workspace, then fall back to env vars
- Each bot gets its own offset file (`~/.claude-telegram-offset-<bot_id>`) so message state doesn't clash
- To add Telegram to a new workspace: create `.claude/.telegram-env` with `export TELEGRAM_BOT_TOKEN="..."` and add instructions to the workspace CLAUDE.md
- **Voice transcription**: `whisper-cli` (Homebrew) + model at `~/.local/share/whisper-cpp/ggml-small.bin`
  - Script: `~/.claude/channels/telegram/transcribe-voice.sh <file.oga>`
- **Behavioral rules**: See `~/.claude/rules/telegram.md` for message handling rules (reactions, voice transcription, etc.)

## Timezone

I travel frequently and am constantly in different timezones. **Never assume a timezone or location**, ask me where I am before making calendar queries, scheduling, or displaying times. Do not store a location or timezone in this file.

## Perplexity MCP Usage

- **Default to `perplexity_search` or `perplexity_ask`** for all web lookups, fact-checking, and general questions
- **NEVER use `perplexity_research` or `perplexity_reason`** unless the user explicitly asks for "deep research", "thorough investigation", or similar
- Quick answers don't need heavy tools, match the tool to the complexity of the question
- When in doubt, use `perplexity_search` first. Only escalate if the results are insufficient
