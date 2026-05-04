# skai

A collection of personal Claude Code skills I use day to day.

## What is a skill

A skill is a slash command for [Claude Code](https://claude.ai/code). Drop a folder with a `skill.md` into `~/.claude/skills/` and it becomes available as `/skill-name` in any session.

## Install

Clone this repo and copy the skills you want:

```bash
git clone https://github.com/lnevespereira/skai
cp -r skai/backlog ~/.claude/skills/
```

## Skills

### /backlog

Keeps a running work log so you remember what you shipped each month. If you use the Jira CLI, pass a ticket ID and it pulls context automatically.

On first use the skill will ask where to store the file. Optionally set `BACKLOG_PATH` to skip that prompt:

```bash
export BACKLOG_PATH=~/notes/backlog.md
```

```
/backlog rewrote the payment service
/backlog added dark mode FEAT-42
```
