# MCP Server Connection — Quick Reference

## What is this?
A reference card for connecting Claude to external tools using MCP (Model Context Protocol).

## How to connect a service

The basic pattern is:
1. Find the MCP server you want (Gmail, Google Calendar, Slack, etc.)
2. Connect it to your Claude Code setup
3. Claude can now use that service

## Example: Connecting Gmail

Once connected, Claude can:
- Search your inbox for specific emails
- Read email content
- Create draft replies
- List messages from specific senders

## Permissions to understand

When you connect an MCP server, you're granting Claude specific abilities:
- **Read access**: Claude can look at your data (emails, calendar events, etc.)
- **Write access**: Claude can create new items (drafts, events) but typically can't send or delete without your approval
- **You stay in control**: You can disconnect any MCP server at any time

## Safety tips

- Only install MCP servers from trusted sources
- Review what access you're granting before connecting
- You can disconnect anytime by removing the server from your settings
- Never connect servers that ask for more access than they need
