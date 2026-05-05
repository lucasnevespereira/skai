# skai

Personal toolkit: Claude Code skills and configs I use day to day.

## What is a skill

A skill is a slash command for [Claude Code](https://claude.ai/code). Drop a folder with a `skill.md` into `~/.claude/skills/` and it becomes available as `/skill-name` in any session.

## Install

Clone this repo:

```bash
git clone https://github.com/lnevespereira/skai
```

## Skills

### /backlog

Keeps a running work log so you remember what you shipped each month. If you use the Jira CLI, pass a ticket ID and it pulls context automatically.

```bash
cp -r skai/skills/backlog ~/.claude/skills/backlog
```

On first use the skill will ask where to store the file. To skip that prompt, set `BACKLOG_PATH` in your shell profile:

```bash
# zsh
echo 'export BACKLOG_PATH=~/notes/backlog.md' >> ~/.zshrc

# bash
echo 'export BACKLOG_PATH=~/notes/backlog.md' >> ~/.bashrc
```

```
/backlog rewrote the payment service
/backlog added dark mode FEAT-42
```

## Configs

### Claude Pulse

My frost-theme Pulse config: compact layout, EUR, 24h clock, no animation.

```bash
mkdir -p ~/.config/claude-status
cp skai/configs/claude-pulse/config.json ~/.config/claude-status/config.json
```

Pulse also needs hooks in `~/.claude/settings.json`. Run `/pulse` in Claude Code to set them up.
