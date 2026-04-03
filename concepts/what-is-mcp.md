# MCP (Model Context Protocol)

## What is it?

Think of MCP as **universal remote adapters**. You know how different TVs, sound bars, and streaming boxes each come with their own remote? MCP is like a universal system that lets one remote (Claude) control all of them. Each adapter connects Claude to a different tool or service.

MCP stands for Model Context Protocol. It's a standard way for Claude to plug into external tools and services -- like your email, calendar, browser, or databases -- so it can read from and interact with them directly.

## Why does it matter?

Without MCP, Claude can only work with what you paste into the conversation. With MCP, Claude can reach out to your actual tools -- checking your calendar, reading your email, browsing a webpage -- making it dramatically more useful for real work.

## How does it work?

- MCP uses a **client-server model**: Claude is the client, and each external tool runs a small server
- You configure which MCP servers to connect in your project settings
- Once connected, Claude can use that tool's capabilities just like any built-in feature
- Each MCP server is built to handle one service (email, calendar, browser, etc.)

## Real-world examples

- **Gmail MCP:** Let Claude read, search, and draft emails directly from your inbox
- **Google Calendar MCP:** Have Claude check your availability and suggest meeting times
- **Browser MCP:** Let Claude visit web pages, fill out forms, and take screenshots
- **Database MCP:** Allow Claude to query your data and pull reports without you writing any code
