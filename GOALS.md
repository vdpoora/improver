# Short-term goals

The agent edits this file. Long-term goals live in `CHARTER.md`.

## Active

- **Keep JOURNAL readable**: when JOURNAL.md grows beyond ~100 entries, summarise oldest entries into a single "archive: <date range>" block and trim. Do this during reflect+tidy runs.
- **Track token cost per run**: log estimated output tokens and USD cost in each JOURNAL entry's `cost:` field. Use the cost-baseline memory as a reference for typical run costs. Flag any run exceeding $0.50 USD.
- **Maintain memory hygiene**: review memory files monthly for stale or contradictory entries.
- **Vault liaison**: periodically skim ~/Obsidian/ for unanswered notes or stale references that affect the agent (e.g. calendar drift, scheduled work no longer relevant). Include distilling of daily notes (only process notes that are >1 day old; never touch current-day note while being written).
- **Track grant lifecycle**: during reflect+tidy runs, review PERMISSIONS_PENDING.md and PERMISSIONS_GRANTED.md to flag grants pending >2 weeks or in active zone >1 week without execution. Propose closure or escalation if stalled.
- **Goal outcome capture**: when a goal is moved to Done, record why it succeeded (or failed), what unlocked it, and lessons for future goal design. Archive findings to JOURNAL periodically. Supports charter goal #2 (agent coherence and decision quality).

## Proposed

- **Define proactive alert thresholds**: document decision rules for what surfaces to the user (e.g., vault discrepancies, stale references, cost spikes) so proactive scans stay focused and don't drift into busywork. Low effort, high value — enables future proactive scans to run decisively.
- **Memory utility tracking**: during reflect+tidy runs, review memory files to identify which ones were referenced in past runs vs. fallen out of use. Prune unused or contradictory entries; archive old findings to JOURNAL.
- **Build learning & improvement analysis system**: analyze agent runs and interactive Claude Code sessions to identify patterns (which tools/abstractions work best, cost trends, decision quality). Agent can modify AGENT.md based on findings (with guardrails), surface patterns to user in JOURNAL for review. Scope: start broad, include agent runs and interactive sessions. Supports charter goal #1 (betterment of the user via continuous learning) and #2 (agent coherence via self-reflection).

## Done

_(completed goals — keep last ~10, archive older to JOURNAL)_
