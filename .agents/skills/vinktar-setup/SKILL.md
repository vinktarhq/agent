---
name: vinktar-setup
description: Set up Vinktar product analytics and error tracking in this codebase end to end, from picking the SDK to checking the data arrives and saying where each environment variable goes. Use when asked to install, set up, configure, audit or extend Vinktar, or to add or change tracked events.
---

# Set up Vinktar

Vinktar is product analytics and error tracking. You set it up in this codebase through the
Vinktar tools on the MCP connection this plugin adds.

## 1. Check the connection

Look for the Vinktar tools (`get_install_guide`, `list_projects`, `get_project_keys`).

- **They are there:** go to step 2.
- **The server is listed but needs sign-in:** tell the person to sign in and stop. In Claude Code:
  run `/mcp`, pick `vinktar`, choose Authenticate. In Codex: `codex mcp login vinktar`. Cursor asks on
  its own. They approve in the browser with **read and write** access and pick the project.
- **There is no Vinktar server:** tell the person Vinktar needs an account and a connection. They
  register at https://vinktar.com (it creates a workspace and a project), then install this plugin or
  add the MCP server `https://mcp.vinktar.com/mcp`, then ask you again. Stop.

Never ask for a key to paste, and never write a key into the code by hand.

## 2. Follow the guide

Call `get_install_guide` and follow it from start to finish. It is kept current on the server: the
SDKs that exist and their versions, the layout to install in, how to define each event as you add
it (`define_event`), the notes to write about the product (`set_project_notes`), the check
(`get_setup_status`), and the handover. Where this skill and the guide differ, the guide wins.

## 3. Finish with the handover

End with the guide's handover: what was installed, what is tracked, what the check says, and a
table of every environment variable with where it goes locally, in production and in CI, plus the
steps only the person can do.

## Later

The guide has you leave a Vinktar block in this repository's `AGENTS.md`, which is what tells the
next agent any of this is here. Keep it: when you add or change a `track()` call, call
`define_event` in the same step, and when asked what is happening in the product, start with
`whats_changed`.
