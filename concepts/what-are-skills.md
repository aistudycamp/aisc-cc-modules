# Skills

## What is it?

Skills are like **recipe cards and reference guides** for Claude. Some are step-by-step workflows you trigger on demand (like a recipe card for a specific dish). Others are reference material Claude draws on when it's relevant (like a style guide on the shelf).

A skill is a markdown file that gives Claude reusable knowledge or workflows. **Action skills** are things you invoke by name, like `write-blog-post`. **Reference skills** load automatically when Claude thinks they'll help -- like your API documentation or coding conventions.

## Why does it matter?

Skills let you get consistent, repeatable results without re-explaining yourself. Once you've dialed in a great workflow for a task, you save it as a skill and reuse it forever.

## How does it work?

- Skills are stored as markdown files inside `.claude/skills/` in your project, each in its own subdirectory with a `SKILL.md` file
- **Action skills** are invoked by typing their name (like `write-blog-post`). Claude reads the instructions and follows them.
- **Reference skills** load automatically when Claude decides they're relevant to what you're working on -- you don't need to invoke them.
- You can set a skill to only load when you invoke it manually, keeping Claude's attention focused.

## Real-world examples

- **Writing blog posts:** A skill that defines your brand voice, target word count, formatting rules, and SEO checklist
- **Analyzing survey data:** A skill that tells Claude how to summarize responses, flag trends, and format a report
- **Generating social media captions:** A skill that specifies platform, tone, hashtag strategy, and character limits
- **Creating meeting agendas:** A skill that pulls in attendees, topics, and time blocks in your preferred format
