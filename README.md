# Vinktar for coding agents

[Vinktar](https://vinktar.com?ref=agent-plugin) is product analytics and error tracking your coding
agent can use. This plugin gives Claude Code, Cursor and Codex two things at once:

- **The Vinktar MCP server** (`https://mcp.vinktar.com/mcp`). You sign in in the browser and choose
  a workspace, optionally one project, and read or read and write. No key to paste.
- **The `setup` skill.** Run `/vinktar:setup` in Claude Code, or ask your agent to "set up Vinktar".
  It reads your repo, installs the SDK for your stack in a standard layout, fetches the project's
  write key over the connection, wires identify, errors and source maps, defines each event it
  tracks, checks what actually arrived, and ends with a list of every environment variable and where
  it goes.

Once it's installed, ask it things like "what changed this week?" or "which errors hit the most
people since the last release?".

You need a Vinktar account first. [Register](https://vinktar.com?ref=agent-plugin); it creates a
workspace and a project.

## Install

**Claude Code**

```sh
claude plugin marketplace add vinktarhq/agent
claude plugin install vinktar@vinktar
```

Then run `/mcp` in a session, pick `vinktar` and authenticate, and run `/vinktar:setup`.

**Cursor**

Install Vinktar from the Cursor Marketplace, or import this repository under Customize → Plugins →
From GitHub Repository. Cursor asks you to sign in the first time it connects.

**Codex**

```sh
codex plugin marketplace add vinktarhq/agent
codex plugin add vinktar@vinktar
codex mcp login vinktar
```

**Any other MCP client**

Add `https://mcp.vinktar.com/mcp` as a Streamable HTTP server; it finds the sign-in on its own. Then
ask your agent to call `get_install_guide`. Setup for each client:
[vinktar.com/docs/mcp](https://vinktar.com/docs/mcp?ref=agent-plugin).

**A harness that reads skills but has no plugin format**

Copy `.agents/skills/vinktar-setup/` into your repository (or your home directory, wherever your
tool looks). It is the same skill, at the path most tools agree on, and it needs the MCP server
added separately.

## What it can and can't do

The agent sees what you'd see in the workspace and project you approved. It can't delete anything,
create projects or keys, manage members or billing, or send data anywhere. Every call is logged on
the project's AI agents page, and an admin can switch agents off.

Vinktar works on every plan, Free included. Data requests count against a monthly allowance;
setting a project up never does, and nothing is charged per call.

## License

MIT
