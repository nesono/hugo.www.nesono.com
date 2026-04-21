---
title: "Copy Confluence Page on a Schedule"
date: 2026-04-18T21:09:38+02:00
---

## What

We use a single Confluence page for our weekly review and our approach is intentionally simple:

- Keep one live page that is updated ahead of each session
- Focus on outcomes, not activities  
    Don’t describe what you did — describe what the product can do now
- After the session, create a read-only snapshot of the page (e.g. weekly, with a date in the title)

That’s it.

You end up with:

- A single source of truth for the current state
- A clean, chronological history of progress over time

## Confluence Automation

You can automate the snapshot step using Confluence Automation:

1. Create a new automation rule (ask an admin if needed)
2. Trigger: Scheduled (e.g. weekly after your session)
3. CQL query: Select the live page  
    Example: `space = <YOUR_SPACE> AND id = <YOUR_PAGE_ID>`
4. Condition (optional): Only run if recently updated  
    Example: `lastmodified >= now("-7d")`
5. Action: Copy the page  
    Add a date to the title (e.g. `{{now().jiraDate()}} Weekly Review`)

Activate the rule — and you’re done.

