# MCP (Model Context Protocol)

## What is it?

So far, everything you've learned has been about what happens *inside* Claude — shaping its behavior, giving it skills, automating with hooks. But what if Claude could reach *out* and interact with your actual tools — your email, your calendar, your browser?

That's what MCP makes possible. Think of it as **universal remote adapters**. You know how different TVs, sound bars, and streaming boxes each come with their own remote? MCP is like a universal system that lets one remote (Claude) control all of them. Each adapter connects Claude to a different tool or service.

MCP stands for **Model Context Protocol** — but you don't need to memorize that. Here's what each word means in plain language: **Model** = the AI (Claude). **Context** = the information and tools it can access. **Protocol** = a standard way of connecting. Put it together: a standard way to connect Claude to outside tools.

## Why does it matter?

Without MCP, Claude can only work with what you paste into the conversation. With MCP, Claude can reach out to your actual tools -- checking your calendar, reading your email, browsing a webpage -- making it dramatically more useful for real work.

## How does it work?

Here's the basic pattern:

1. **Someone builds an adapter** for a specific tool (Gmail, Google Calendar, a database, etc.). This adapter is called an MCP server — it knows how to talk to that tool.
2. **You plug the adapter in** by adding it to your project settings. You do it once, and it's connected.
3. **Claude uses the tool through the adapter.** When you ask "What's on my calendar today?", Claude sends that question to the calendar adapter, gets the answer, and reports back.

The key idea: Claude asks, the adapter answers. You can plug in as many adapters as you want — one for email, one for your calendar, one for a database — and Claude can use all of them. People are building new adapters all the time, which means Claude keeps getting more capable.

## Real-world examples

- **Gmail MCP:** Let Claude read, search, and draft emails directly from your inbox
- **Google Calendar MCP:** Have Claude check your availability and suggest meeting times
- **Browser MCP:** Let Claude visit web pages, fill out forms, and take screenshots
- **Database MCP:** Allow Claude to query your data and pull reports without you writing any code

## Quick check

A coworker asks you: "How is an MCP server different from just pasting information into the chat?" What would you tell them?

*(The key difference: pasting gives Claude a snapshot of old information. An MCP server gives Claude live access — it can look things up right now, not just read what you copied.)*
