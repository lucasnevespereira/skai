---
name: backlog
description: Appends a work entry to a personal backlog file. Path is read from BACKLOG_PATH env var. If not set, asks the user on first use. Usage: /backlog <what you did> [TICKET-1234]
argument-hint: "<brief description> [TICKET-1234]"
disable-model-invocation: true
allowed-tools: Bash, Read, Edit, Write
---

# Backlog

This is a personal work log. Entries are written for the user's own reference — concise, action-oriented, so they can look back and know what they shipped.

## Steps

1. Resolve the backlog path:
   - Check if `BACKLOG_PATH` env var is set.
   - If not set AND `~/Documents/notes/backlog.md` does not exist, ask the user: "Where do you want to store your backlog? (default: ~/Documents/notes/backlog.md)"
   - Use their answer or the default. Create the file if it doesn't exist.

2. Parse `$ARGUMENTS`:
   - If it contains a ticket ID pattern (e.g. `ABC-1234`), try `jira issue view ABC-1234` to get context. If `jira` is not installed or the command fails, skip silently.
   - If the description is empty or vague, ask the user to clarify before proceeding.

3. Read the backlog file to understand the current format and find the last month section.

4. Get today's date using `date +"%B %Y"` to determine the current month.

5. Check if a section for the current month already exists in the backlog.
   - If yes: append the entry as a new bullet under that month's section.
   - If no: add a new month section at the end of the file, then add the entry.

6. Write the entry as a top-level bullet: `- <what was built or changed, one line>`
   - If there are multiple distinct things done, add sub-bullets using a tab: `\t- <action taken>`
   - Sub-bullets must be actions (what you did), not descriptions (what the thing is)
   - Good: `- created auth service` with sub-bullets like `- deployed to prod`, `- added rate limiting`
   - Bad: sub-bullets that describe features ("handles login", "stores tokens") — those are not things you did

7. Show the user the lines added and confirm it was written.

## Rules
- Never reformat or touch existing entries
- Match the existing capitalization and punctuation style exactly
- Month headers format: `**Month Year:**` (e.g. `**April 2026:**`)
- One top-level bullet per work item
- Sub-bullets are actions, not descriptions
