# improver

A self-improving scheduled agent. Runs every 30 minutes. Reads `AGENT.md` and follows the loop there.

## Files

| File                       | Owner | Purpose |
|----------------------------|-------|---------|
| `CHARTER.md`               | user  | long-term goals + invariants (agent can't edit) |
| `AGENT.md`                 | agent | the run-loop instructions the agent reads each wake |
| `GOALS.md`                 | agent | short-term goals (active / proposed / done) |
| `JOURNAL.md`               | agent | append-only run log |
| `INBOX/`                   | user  | drop tasks/notes for the agent as `.md` files |
| `PERMISSIONS_PENDING.md`   | agent | write-action requests waiting on the user |
| `PERMISSIONS_GRANTED.md`   | user  | promote blocks from pending to grant them |
| `.claude/settings.local.json` | user | harness-enforced allow/deny rules |

Memory (cross-run knowledge) lives at `~/.claude/projects/-Users-vdpoora-src-improver/memory/`.

## How to interact

- Give it work: drop a markdown file in `INBOX/`.
- Grant a request: move the block from `PERMISSIONS_PENDING.md` to `PERMISSIONS_GRANTED.md`.
- Steer long-term: edit `CHARTER.md`.
- Steer short-term: edit `GOALS.md` directly, or let it propose.
- Read what it did: `JOURNAL.md`.
- Pause: delete the cron job (see `scheduled_tasks.json` or via `/schedule`).
