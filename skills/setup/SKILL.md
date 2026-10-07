---
name: setup
description: Set up Vinktar product analytics and error tracking in this codebase end to end, from picking the SDK to checking the data arrives and saying where each environment variable goes. Use when asked to install, set up, configure, audit or extend Vinktar, or to add or change tracked events.
---

# Set up Vinktar

Vinktar is product analytics and error tracking. You set it up in this codebase through the
Vinktar tools on the MCP connection this plugin adds.

## 1. Get connected

Look for the Vinktar tools (`get_install_guide`, `list_projects`, `get_project_keys`). Their names
carry a prefix that differs from app to app.

- **They are there:** go to step 2.
- **A Vinktar tool whose name ends in `authenticate` is there instead:** call it. It returns a
  sign-in link. Give the link to the person, wait until they say they approved, then go to step 2.
- **A Vinktar server or connector is listed as needing sign-in, with no such tool:** signing in is
  the one step only the person can do, so say exactly where, for the app you are running in:
  - Claude Code in a terminal: `/mcp`, pick `vinktar`, choose Authenticate.
  - Claude Desktop and Cowork: open Customize, find Vinktar, and connect its `vinktar` connector.
  - Codex: `codex mcp login vinktar`. Cursor asks on its own.

  In the browser they sign in to Vinktar, or make an account there on the spot, leave Build and
  Configure switched on, and approve. Then carry on from step 2 without being asked again.
- **There is no Vinktar server at all:** tell the person to install this plugin or add the MCP
  server `https://mcp.vinktar.com/mcp`, then ask you again. Stop.
- **No codebase is open** (a chat with no project, a phone): the install needs the code, so say
  that, and ask the person to open their project in Claude Code or the Code tab and ask again. If
  their app already reports to Sentry or Bugsnag, `get_project_keys` has the line that points it at
  Vinktar, which they can paste themselves.

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

Before adding an event to an app that is already set up, call `get_install_guide` with
`section: "conventions"`. The short version: event names and property keys are `snake_case`, object
then past-tense action (`report_exported`); a description is one sentence; a name never changes its
meaning, so a new meaning gets a new name.
