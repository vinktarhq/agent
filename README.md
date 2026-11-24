# Vinktar for coding agents

[Vinktar](https://vinktar.com?ref=agent-plugin) is error tracking your coding agent can read, with what
the user did right before each error. This plugin gives Claude Code, Cursor and Codex three things:

- **The Vinktar MCP server** (`https://mcp.vinktar.com/mcp`). You sign in in the browser and choose
  a workspace, the projects it may reach, and read, build or configure. No key to paste.
- **The `setup` skill.** Run `/vinktar:setup` in Claude Code, or ask your agent to "set up Vinktar".
  It reads your repo, installs the SDK for your stack in a standard layout, fetches the project's
  write key over the connection, wires identify, errors and source maps, defines each event it
  tracks, checks what actually arrived, and ends with a list of every environment variable and where
  it goes.
- **The `/vinktar` command.** Type `/vinktar` to set Vinktar up in this repo, or once it is set up
  to hear what broke. `/vinktar what broke after the last deploy?` asks a question directly.

Once it's installed, ask it things like "what changed this week?" or "which errors hit the most
people since the last release?".

You don't need an account beforehand: the sign-in makes one on the spot.

## Install

**Claude Code**

```sh
claude plugin marketplace add vinktarhq/agent
claude plugin install vinktar@vinktar
```

Run `/mcp`, pick `vinktar` and authenticate, then run `/vinktar:setup`.

**Claude (claude.ai, the desktop app, Cowork)**

Adding the plugin does not connect Vinktar. After you add it:

1. Open the plugin's Connectors tab, or
   [claude.ai/customize/connectors](https://claude.ai/customize/connectors), and choose Connect next
   to Vinktar.
2. Sign in or make a free account in the browser, leave Build and Configure on, and approve.
3. Start a new chat. A chat that was already open does not pick up the connection.

Then ask "what broke today?", or type `/vinktar`.

**Cursor**

Import this repository under Customize → Plugins → From GitHub Repository. Cursor asks you to sign in the first time it connects.

**Codex**

```sh
codex plugin marketplace add vinktarhq/agent
codex plugin add vinktar@vinktar
codex mcp add vinktar --url https://mcp.vinktar.com/mcp
```

The last line adds the connection and opens the sign-in in your browser.

**Any other MCP client**

Add `https://mcp.vinktar.com/mcp` as a Streamable HTTP server; it finds the sign-in on its own. Then
ask your agent to call `get_install_guide`. Setup for each client:
[vinktar.com/docs/mcp](https://vinktar.com/docs/mcp?ref=agent-plugin).

**A harness that reads skills but has no plugin format**

Run `npx skills add vinktarhq/agent` in your project, or copy `.agents/skills/setup/` into your
repository (or your home directory, wherever your tool looks). It is the same skill, at the path most tools agree on, and it needs the MCP server
added separately.

## What it can and can't do

The agent sees what you'd see in the workspace and project you approved. The only things it can
delete are boards and panels, and those stay restorable from the boards page for 30 days. It can't
delete events, errors, issues or projects, create projects or keys once you are signed in, manage
members or billing, or add somewhere new to send your data. Every call is logged on the project's AI agents page, and an
admin can switch agents off.

Vinktar works on every plan, Free included. Data requests count against a monthly allowance;
setting a project up never does, and nothing is charged per call.

## License

MIT
