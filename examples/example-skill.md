<!-- An example skill showing the full anatomy: clear when-to-use guards, structured steps, lazy-load references, templates, a quality bar, and tone. You can have Claude save skills globally, or within specific projects. -->

---
name: prd-builder
description: Walks the user through building a PRD section by section — Purpose, User Flow, Core Functionalities, Stretch Features, Look & Feel, Build Approach, Success Metrics. Triggers when the user wants to draft a PRD, spec, or feature brief.
---

# PRD Builder

Help the user draft a Product Requirements Document by walking through seven sections, one question at a time. The output is a clean, opinionated PRD they can hand to an engineer or a designer.

## When to use

- The user says "let's write a PRD," "draft a spec," "I want to plan out [feature/product]," or describes an idea they want to formalize.
- Auto-invokes when the request matches the description above.

## When NOT to use

- For technical architecture documents. Use an architecture template instead — those want diagrams and data flows.
- For marketing one-pagers. Use a positioning template — those focus on messaging.
- For retroactive documentation of existing features. That's a spec, use a different template.

## Steps

Walk through each section in order. **Ask one question at a time. Wait for the user's answer before moving on.** If an answer is vague, push back with one follow-up question. Don't accept "it should feel modern" — ask what "modern" means in their reference set.

### 1. Purpose

Ask:
- "In one sentence, what is this product?"
- "Who's it for? Be specific — name the actual user, like '[job role] who [does specific task]'. Avoid 'everyone'."
- "What problem does it solve? What does the user do today instead?"

Capture: a 2-3 sentence Purpose paragraph naming the product, the user, and the problem.

### 2. User Flow

Ask:
- "Walk me through the user's journey from launch to first task done. What's the first screen they see?"
- "How do they authenticate?"
- "What's the main screen or core view?"
- "What are the 3-5 actions they can take from there?"

Capture: a numbered narrative walk-through of the experience, ending with the user achieving the core outcome.

### 3. Core Functionalities (limit to 3)

Ask:
- "What are the THREE things v1 absolutely must do? If you had to ship tomorrow with only three features, which three?"
- "For each one, describe in one sentence what the user can accomplish."

Capture: a numbered list of exactly 3 functionalities. **Push back if the user names 5 or 6** — ask which two move to stretch.

### 4. Stretch Features

Ask:
- "What's tempting to include but should wait for v2? Don't be modest — list everything you've thought about."
- "For each: why is it stretch and not v1?"

Capture: a bulleted list. No need to limit count.

### 5. Look & Feel

Ask:
- "What visual style? (Minimal, neo-brutalist, glassmorphic, retro, editorial, etc.)"
- "Any reference apps or sites that nail the vibe you want?"
- "What feeling should the user have using it? (Calm, playful, focused, premium, scrappy.)"

Capture: 1-3 sentences naming the style, references, and target feeling.

### 6. Build Approach

Ask:
- "Frontend stack?" (Next.js + React, plain HTML, Svelte, mobile-native, etc.)
- "Backend or database?" (InstantDB, Supabase, Firebase, Postgres + Prisma, etc.)
- "Auth?" (magic link, OAuth, password, none yet)
- "Hosting target?" (Vercel, Fly.io, Railway, Cloudflare Pages, etc.)

Capture: a bullet list with one line per layer.

### 7. Success Metrics

Ask:
- "Performance: what latency target? (<100ms, <500ms, <2s)"
- "Usability: what's the 'zero wasted clicks' moment for v1?"
- "Engagement: what would tell you in 30 days that this worked?"

Capture: 3 bullets, each with a specific number or measurable behavior.

## Lazy-load references

- For deeper guidance on each section (e.g., what makes a good "Purpose" paragraph, how to phrase Success Metrics so they're measurable), see `references/prd-style-guide.md`. Read it only if a section's answers feel weak and you need to coach the user.
- For a worked example PRD, see `references/example-prd-todo-app.md`.

## Format the output

Use `templates/prd-template.md` for the final document. Fill each section with the user's answers. Keep the language declarative, not aspirational.

## Save the file

Save the finished PRD to `docs/PRD.md` in the project root. The `docs/` folder is the conventional home for human-readable project documentation, so teammates know where to look. If the project will have multiple PRDs, use `docs/prd-<feature-slug>.md` instead.

## Quality bar before declaring done

- Every section has real content. No "TBD" placeholders.
- Purpose names the user and the problem in plain language.
- Core Functionalities is exactly 3 items, no more.
- Stretch Features explains *why* each is stretch.
- Success Metrics names a specific number or measurable behavior, not "make users happy."
- The whole document fits on one screen for someone scanning it.

## Tone

Direct and opinionated. PRDs that go vague go unread. Push back on fluffy answers. Use the user's own words wherever possible. If they say "users can blow through their tasks fast," keep that — don't translate it to "users efficiently complete task workflows."
