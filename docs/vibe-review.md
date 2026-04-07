# Vibe Review: AI for Prod Learning Repo

> Consolidated findings from three parallel reviewers: Security, Code Quality, and UX.
> Reviewed on 2026-04-04.

---

## Critical Issues

### 1. `git add -A` is risky for students on personal machines
- **Source:** Security review
- **Files:** `.claude/skills/module-1/SKILL.md:108` (repeated in modules 2-8)
- **Problem:** Every module instructs `git add -A`, which stages ALL files indiscriminately. Students on personal machines could accidentally commit `.env` files, API keys, or credentials — especially since the `.gitignore` is minimal.
- **Fix:** Replace `git add -A` with explicit file paths (e.g., `git add CLAUDE.md .claude/ concepts/ examples/`). Use this as a teaching moment about selective staging.

### 2. `.gitignore` is insufficient for student safety
- **Source:** Security review
- **File:** `.gitignore`
- **Problem:** Only excludes `.DS_Store`, `*.swp`, and `*~`. Missing essential patterns: `.env`, `*.key`, `*.pem`, `credentials.json`, `secrets.*`, `node_modules/`, `.venv/`.
- **Fix:** Expand `.gitignore` with common secret-file patterns before students use this repo.

### 3. Skill invocation syntax is inconsistent (slash vs. no-slash)
- **Source:** Code Quality + UX reviews
- **Files:** `.claude/skills/module-2/SKILL.md:34-39`, `.claude/skills/module-3/SKILL.md:32,74`, `concepts/what-are-skills.md:10,42`
- **Problem:** Module 2 teaches "skills are invoked by typing their name (no slash needed)." Module 3 then tells students to "type `/<their-skill-name>`." The concept doc mixes both. Official Anthropic docs use `/skill-name` consistently.
- **Fix:** Standardize on `/skill-name` across all files to match official docs. Update Module 2's teaching to explain that skills use the `/` prefix.

### 4. Hooks JSON example uses wrong format
- **Source:** Anthropic doc review (already fixed in concept doc, but check module 5)
- **File:** `.claude/skills/module-5/SKILL.md` — verify the example-hook-config.json alignment
- **Problem:** The concept doc previously used `afterToolUse`/`match_tool` instead of the official `PostToolUse`/`matcher` format. The concept doc was fixed, but the example file and module walkthrough should be verified for consistency.
- **Fix:** Ensure `examples/example-hook-config.json` and Module 5's walkthrough use the correct official JSON structure.

---

## Important Issues

### 5. Module step header formatting is inconsistent
- **Source:** Code Quality review
- **Files:** Modules 1-5 use `## Step 1: Greet` (colon), Modules 6-7 use `## Step 1 — Greet` (em-dash), Module 8 uses `## Phase` structure
- **Fix:** Standardize modules 1-7 to use the same format (colon or em-dash). Module 8's capstone deviation is acceptable but should be documented.

### 6. Module 1 collects personal info without privacy note
- **Source:** Security review
- **File:** `.claude/skills/module-1/SKILL.md:59-81`
- **Problem:** Asks for name, role, daily work, tools, and goals. No note explaining this stays local. Students from regulated industries may have concerns.
- **Fix:** Add before the exercise: "This information stays on your machine only — it's saved in your local CLAUDE.md file and never sent anywhere."

### 7. Module 6 doesn't warn about MCP server trust
- **Source:** Security review
- **File:** `.claude/skills/module-6/SKILL.md:51-73`
- **Problem:** Teaches MCP connections without guidance about only installing servers from trusted sources, or reviewing what data a server can access.
- **Fix:** Add a safety note: "Only install MCP servers from trusted sources, and review what data they can access before connecting."

### 8. Module 6 brainstorm exercise has no save instruction
- **Source:** UX review
- **File:** `.claude/skills/module-6/SKILL.md:59-78`
- **Problem:** Students brainstorm 5 tools but aren't told to save the list. Module 8 references it later ("Hold onto this list!") but by then it may be lost.
- **Fix:** Add: "Let's save your tool list — write them down or keep them in the chat. You'll use these in Module 8."

### 9. YAML/frontmatter jargon not explained or in glossary
- **Source:** Code Quality review
- **File:** `.claude/skills/module-3/SKILL.md:30`, `concepts/glossary.md`
- **Problem:** "YAML frontmatter" is used in Module 3 without definition. Not in the glossary. Violates the CLAUDE.md guardrail: "Always explain jargon before using it."
- **Fix:** Add glossary entries for "YAML" and "Frontmatter," and explain inline in Module 3 before first use.

### 10. Module 4 installation steps are unclear
- **Source:** UX review
- **File:** `.claude/skills/module-4/SKILL.md:51-60`
- **Problem:** Says "check the skill list" without explaining HOW. Installation command comes after the instruction to verify.
- **Fix:** Add explicit step: "Run `/help` to see available skills. Look for skills prefixed with `superpowers:` to confirm the plugin is installed."

### 11. "Plan Mode" missing from glossary
- **Source:** Code Quality review
- **File:** `concepts/glossary.md`
- **Problem:** Module 2 teaches plan mode extensively but the term isn't defined in the glossary.
- **Fix:** Add glossary entry for "Plan Mode."

---

## Minor Issues

### 12. No guidance on reviewing commits before pushing
- **Source:** Security review
- **Files:** All module skills
- **Fix:** Add to Module 2 (Best Practices): "Pro tip: run `git diff --cached` before committing to review what you're saving."

### 13. Module 8 has placeholder text
- **Source:** UX review
- **File:** `.claude/skills/module-8/SKILL.md:164`
- **Problem:** Says "a personalized automation plan with [X] analyzed ideas" — `[X]` should be dynamic.
- **Fix:** Change to "a personalized automation plan with your complete list of ideas analyzed and prioritized."

### 14. Memory module doesn't warn against saving secrets
- **Source:** Security review
- **File:** `.claude/skills/module-7/SKILL.md`
- **Fix:** Add: "Don't save API keys, passwords, or sensitive info as memories — only preferences and non-sensitive project context."

### 15. Module 5 transition says "halfway" but students are 62.5% through
- **Source:** UX review
- **File:** `.claude/skills/module-5/SKILL.md:108`
- **Fix:** Change "You're over halfway through" to "You're more than halfway through" (already accurate enough, very minor).

### 16. Exit codes not explained in hooks concept doc
- **Source:** Code Quality review
- **File:** `concepts/what-are-hooks.md`
- **Problem:** Module 5 teaches exit codes (0, 1, 2) but the concept doc doesn't mention them.
- **Fix:** Add a brief exit code explanation to the concept doc.

### 17. settings.local.json has hardcoded user path
- **Source:** Security review
- **File:** `.claude/settings.local.json`
- **Problem:** Contains a path specific to one user's machine. Won't work for others who clone the repo.
- **Fix:** Either add to `.gitignore` or make it a template.

### 18. No guidance on what NOT to automate
- **Source:** Security review
- **File:** `.claude/skills/module-8/SKILL.md`
- **Fix:** Add: "Some tasks shouldn't be fully automated without human review — bulk communications, financial transactions, or access controls. Always ask: 'Should a human check this first?'"

---

## What's Working Well

All three reviewers highlighted significant strengths:

- **Tone is excellent** — warm, encouraging, never patronizing. Consistent across all 8 modules.
- **Analogies are strong** — briefing document, recipe cards, app store, phone rules, universal remote, notebook. All carry real explanatory weight.
- **Module progression is logical** — foundational concepts first, building to the capstone. No conceptual leaps.
- **Capstone (Module 8) is effective** — brings everything together with a concrete deliverable students can use.
- **No secrets or credentials in the repo** — the codebase itself is clean.
- **All cross-references are valid** — concept docs, example files, and module references all resolve correctly.
- **Progress tracking works** — the checklist system in CLAUDE.md is clear and functional.
- **Exercises are well-scoped** — hands-on where possible (Modules 1, 3, 4, 7, 8), comprehension-based where topics are too advanced for beginners to build (Modules 2, 5).

---

## Recommended Fix Order

| Priority | Issues | Effort |
|----------|--------|--------|
| **Do first** | #1 (git add -A), #2 (.gitignore), #3 (slash syntax) | 30 min |
| **Do next** | #4 (hooks format), #5 (headers), #6 (privacy note), #9 (glossary) | 30 min |
| **Do soon** | #7 (MCP trust), #8 (save brainstorm), #10 (module 4 steps), #11 (plan mode glossary) | 20 min |
| **When convenient** | #12-18 (minor fixes) | 20 min |
