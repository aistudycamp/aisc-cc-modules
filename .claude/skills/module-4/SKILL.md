---
name: module-4
description: "Module 4: Plugins — Discover how to extend Claude Code with community-built plugins"
---

# Module 4: Plugins

You are running an interactive lesson for an AI Study Camp student. Follow the Greet, Teach, Show, Exercise, Celebrate pattern below. Be a warm, encouraging coach throughout.

---

## Step 1: Greet

Welcome the student to Module 4 with enthusiasm:

> "Welcome to Module 4! In the last module, you built a skill from scratch -- nice work. Now imagine if someone had already built dozens of useful skills and bundled them together for you to install in one click. That's exactly what plugins are, and you're about to get your hands on one!"

---

## Step 2: Teach

Explain plugins using the "app store" analogy:

- Think about your phone. It comes with some basic built-in apps, but when you want to do something new -- edit photos, track workouts, learn a language -- you go to the app store and install something someone else built. Plugins work the same way for Claude Code.
- A plugin is the **packaging layer** for Claude Code extensions. It can bundle together skills, MCP server connections, and configurations into a single installable unit. Instead of setting everything up yourself from scratch, you install a plugin and get a whole set of new capabilities instantly.
- Why this matters: remember how in Module 3 you created one skill? That was great for learning! But imagine needing 10 or 20 skills for your workflow, plus MCP connections to your tools. Writing and configuring each one from scratch would take a long time. Plugins let you stand on other people's shoulders.
- This is the pattern we introduced in Module 2: **discover first, customize if needed, build only as a last resort.** In Module 3, you searched for individual skills. Plugins take that one step further — instead of finding one skill at a time, you can install a whole toolkit that someone has curated and tested.
- Plugins are installed into your project's `.claude/` folder, and once installed, all their features become immediately available. Plugin skills are namespaced (like `superpowers:brainstorm`) so multiple plugins can coexist without conflicting.

Tell the student:

> "If you want to go deeper later, there's a concept doc at `concepts/what-are-plugins.md`. The easiest way to read it is to just ask me: *'Show me the concept doc on plugins'* — I'll pull it up and walk you through it."

---

## Step 3: Show

Walk the student through what's out there and how installation works:

1. **Give concrete examples of plugins that exist.**
   - **superpowers** -- adds advanced planning, brainstorming, debugging, and code-review workflows. You get slash commands like `/brainstorm`, `/plan`, and `/code-review` all from one install.
   - **frontend-design** -- helps you build polished, production-quality web interfaces with modern design patterns.
   - **playwright** -- adds browser automation for testing websites, taking screenshots, and checking UI behavior.
   - And many more being created by the community all the time.

2. **Show how installation works.** Installing a plugin is done through the Claude Code CLI:
   - Browse and install with `/install-plugin`, or run `claude plugin add <plugin-name>` in your terminal.
   - Once installed, the plugin's skills show up as new slash commands you can use immediately.

---

## Step 4: Exercise

Now the student gets hands-on with plugins:

1. **Discover what's available.** Tell the student: "Let's explore what plugins you could add to your setup." Show them how to look at available plugins. Point out that they may already have some plugins installed -- check the list of available skills in the current session.

2. **Install the plugins we'll use.** We're going to use TWO plugins together so the student can feel what "installing capabilities" really means:
   - **superpowers** — gives us `/brainstorm`, a structured brainstorming workflow.
   - **frontend-design** — generates real HTML mockups the student can view in a browser.

   For each plugin, check the skill list first. If it's already available, say something like: "Great news — superpowers is already installed in this environment, so we can jump right in." If it needs to be installed, walk them through `/install-plugin` or `claude plugin add <plugin-name>` step by step.

3. **Do a real exercise that uses both plugins.** The student is going to redesign a well-known app — by default, use **Instagram**, but let them pick any app they know well (TikTok, Spotify, Gmail, etc.) if they'd rather.

   **Part A — Brainstorm with superpowers.** Have them run `/brainstorm` with a prompt like:

   > "Brainstorm 3 very different new visual design directions for Instagram's home feed. Each one should feel distinct — think 'minimalist', 'playful', 'editorial', 'retro', etc."

   Let the brainstorm skill walk them through it. At the end, make sure you have 3 clearly distinct design directions written down.

   **Part B — Render with frontend-design.** Now take those 3 directions and ask the frontend-design skill to build them as 3 separate HTML files (one per direction), saved to `student-output/module-4/`. Each file should be a single-page mockup of the chosen app's home screen styled in that direction.

   ⚠️ **Important — be explicit with frontend-design about output format.** When you invoke it, tell it: *"produce 3 standalone HTML files only — do not start a dev server, do not scaffold a Next.js or any other project. Just write the three `.html` files to `student-output/module-4/`."* Otherwise it will spin up a dev server in addition to writing the files, which we don't need for this exercise.

   A good prompt for frontend-design looks like:

   > *"Build 3 standalone HTML mockups of [app]'s home feed — one per design direction below. Save them as `design-1.html`, `design-2.html`, `design-3.html` in `student-output/module-4/`. **Do not start a dev server. Do not scaffold a project. Single HTML files only — inline CSS is fine.** Open them with `open` when done.*
   >
   > *Direction 1: [their direction]*
   > *Direction 2: [their direction]*
   > *Direction 3: [their direction]"*

   **Part C — View in the browser.** ⚠️ **Don't stop after the files are generated** — the student has no idea how to view raw HTML files yet. Walk them all the way through to "I can see the mockups in my browser" before moving on.

   Do this proactively, in order:

   1. **Open them yourself with the Bash tool.** On macOS, run:
      ```bash
      open student-output/module-4/design-1.html
      open student-output/module-4/design-2.html
      open student-output/module-4/design-3.html
      ```
      Each `open` command launches that file in the student's default browser. (On Linux, use `xdg-open`; on Windows, use `start`.)

   2. **Give them a copy-paste fallback** in case `open` doesn't work in their setup. Print the absolute paths and tell them:

      > "If those didn't pop open automatically, here's plan B — copy any of these paths and paste it directly into your browser's address bar. That'll open the file:
      >
      > `file:///absolute/path/to/student-output/module-4/design-1.html`
      > `file:///absolute/path/to/student-output/module-4/design-2.html`
      > `file:///absolute/path/to/student-output/module-4/design-3.html`
      >
      > (You can also drag the file from Finder/Explorer straight into a browser window — same result.)"

      Use `pwd` first to get the absolute path of the current project so the `file:///` URLs you print are real and clickable.

   3. **Confirm they can see the mockups.** Don't move on until the student says "yes, I see them." If they want them side-by-side, suggest opening all three in separate browser tabs.

   After they've seen the mockups, do the reveal:

   > "Look what just happened — *you* brainstormed the directions, and two community-built plugins did the heavy lifting. Superpowers structured your thinking. Frontend-design turned it into real, viewable HTML. You didn't write a single line of CSS, and you didn't build either of those workflows yourself. That's the power of plugins — you stood on other people's shoulders."

4. **Success criteria:** The student understands what plugins are, has two plugins available in their setup (superpowers and frontend-design), and has viewed three app-redesign mockups in their browser that they produced by chaining `/brainstorm` into frontend-design. Confirm this with them.

---

## Step 5: Celebrate + Advance

Celebrate their progress with genuine enthusiasm:

> "You just supercharged your Claude Code setup! You went from building one skill yourself to tapping into a whole ecosystem someone else already built. That's a real unlock — you're really getting the hang of this."

Then do these three things:

1. **Update the progress checklist** in CLAUDE.md by changing `- [ ] Module 4: Plugins` to `- [x] Module 4: Plugins`

2. **Save their work with git.** Run the following commands (use the Bash tool):
   - `git add CLAUDE.md .claude/ student-output/`
   - `git commit -m "Complete Module 4 — installed plugins and built 3 app-redesign mockups"`

   Tell the student: "Progress saved!"

3. **Direct them to the next module:**
   > "Module 5 is about MCP Servers -- how Claude connects to external tools and data sources like Gmail, Google Calendar, and databases. It's where Claude stops being just a conversation and starts actually doing work with your tools. Type `module-5` when you're ready!"
