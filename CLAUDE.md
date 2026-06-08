# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

Not a software project. It is the control surface for a self-modifying, scheduled Claude agent. The "source" is markdown: instructions, state, and an append-only log. A `launchd` job fires `claude -p` in this directory on a cron, the agent reads its own instructions, does one thing, logs it, commits, and exits. There is no build, no test suite, no lint.

Two distinct execution modes share these files:
- **Autonomous runs**: scheduled by `~/Library/LaunchAgents/io.factry.improver.plist` (outside the repo). The agent runs as Haiku with `--permission-mode bypassPermissions`, scoped by `AGENT.md` and `.claude/settings.local.json` rather than by the permission prompt.
- **Interactive use**: the user invokes Claude directly to steer the agent (edit CHARTER/AGENT, review grants, change schedule). The same settings still gate writes.

## Architecture (file ownership matrix)

The roles matter more than the contents. Ownership determines who may edit what:

| File / dir | Owner | Role |
| --- | --- | --- |
| `CHARTER.md` | user | invariants + long-term goals; **agent is denied write** via `.claude/settings.local.json` |
| `AGENT.md` | agent | the run-loop the agent reads each wake; self-modifiable with `.bak.<ISO>` backups |
| `GOALS.md` | agent | short-term goals (Active / Proposed / Done) |
| `JOURNAL.md` | agent | append-only run log; older entries get summarised during reflect+tidy runs |
| `INBOX/*.md` | user → agent | user drops tasks here; agent deletes after handling |
| `PERMISSIONS_PENDING.md` | agent appends, user reviews | agent's outbound requests for writes outside its zone |
| `PERMISSIONS_GRANTED.md` | user moves blocks here | active grants the agent consumes, then moves to `## Consumed` |
| `.claude/settings.local.json` | user | hard allow/deny that constrains the agent in autonomous mode; **agent is denied write** |

The permission-request protocol (pending → granted → consumed) is the only sanctioned path for the agent to act outside its own dir. Treat it as the contract — don't shortcut it even when an interactive user is present, because the autonomous run will have no human to ask.

Memory lives **outside** the repo at `~/.claude/projects/-Users-vdpoora-src-improver/memory/` and is part of the agent's allowed write zone.

## Common operations

The agent's run loop is fully specified in `AGENT.md` — read it before touching anything. The non-obvious bits:

- **Schedule changes**: cron lives in `~/Library/LaunchAgents/io.factry.improver.plist`, outside the repo. Reload after editing: `launchctl unload ~/Library/LaunchAgents/io.factry.improver.plist && launchctl load ~/Library/LaunchAgents/io.factry.improver.plist`. The plist uses `StartInterval` (seconds). Per the charter, the agent itself must not edit cron — only the user (or interactive Claude on the user's behalf) does this. Then update the cadence string in `AGENT.md:3` and `README.md:3` to match.
- **Watching runs**: `.logs/run.<YYYY-MM-DD>.jsonl` (stream-json from `claude -p`), plus `.logs/run.err` and `.logs/launchd.{out,err}`. Cost per run is in the final `result` event's `total_cost_usd`.
- **Granting a request**: move a block from `PERMISSIONS_PENDING.md` to the `## Active grants` section of `PERMISSIONS_GRANTED.md`. The next autonomous run consumes it and moves it to `## Consumed`.
- **Committing**: the agent commits and pushes `origin main` itself at the end of every run. Never force-push. If your interactive changes overlap with what the agent might write, commit immediately to avoid races.
- **Cost model**: at the time of writing, ~$0.07/run on Haiku 4.5 (mostly cached-input reads). Output tokens are the lever; the per-run target is <50k output, hard ceiling 200k (charter invariant).

## Hard constraints (from CHARTER + settings)

- Agent writes are restricted to `~/src/improver/**` (excluding `CHARTER.md` and `.claude/`) and the memory dir. Anything else needs a grant.
- No `curl`/`wget`, no `rm -rf`, no force-push, no `git reset --hard`, no `git checkout --`, no `git clean`. These are denied in `settings.local.json`.
- Never commit or push in any other repo (notably the Obsidian vault at `~/Obsidian/`, which has its own backup sweep).
- Never write secrets to any file in this repo — it pushes to `git@github.com:vdpoora/improver.git`.

## Self-modification

`AGENT.md` is the agent's own source of behaviour. Before editing it (interactively or autonomously), copy current contents to `AGENT.md.bak.<ISO>` and keep at most the 5 most recent backups. If a run starts and `AGENT.md` produces no coherent plan, the run should revert to the latest `.bak` and log the revert rather than continue.
