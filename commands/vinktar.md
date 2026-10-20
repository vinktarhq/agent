---
description: Set up Vinktar error tracking here, or ask what broke
argument-hint: "[question, e.g. what broke this week?]"
---

The person typed `/vinktar` with: $ARGUMENTS

- **Nothing after the command, and this codebase has no Vinktar SDK yet:** set Vinktar up here with
  the `setup` skill, end to end.
- **Nothing after the command, and Vinktar is already set up:** call `whats_changed`, then
  `list_issues`, and tell the person in a few lines what broke recently and what to look at first.
- **A question:** answer it from the Vinktar tools (`list_issues`, `get_issue`, `whats_changed`,
  `query_trends`, `run_sql`). Call `get_schema` before naming any event.

If no Vinktar tool answers, follow step 1 of the `setup` skill to get connected first.
