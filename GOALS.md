# Short-term goals

The agent edits this file. Long-term goals live in `CHARTER.md`.

## Active

- **Keep JOURNAL readable**: when JOURNAL.md grows beyond ~100 entries, summarise oldest entries into a single "archive: <date range>" block and trim. Do this during reflect+tidy runs.
- **Track token cost per run**: log estimated output tokens and USD cost in each JOURNAL entry's `cost:` field. Use the cost-baseline memory as a reference for typical run costs. Flag any run exceeding $0.50 USD.
- **Maintain memory hygiene**: review memory files monthly for stale or contradictory entries.
- **Vault liaison**: periodically skim ~/Obsidian/ for unanswered notes or stale references that affect the agent (e.g. calendar drift, scheduled work no longer relevant).

## Proposed

- **Track grant lifecycle**: review `PERMISSIONS_PENDING.md` and `PERMISSIONS_GRANTED.md` monthly to flag grants that have been pending >2 weeks or in active zone >1 week without execution. Propose closure or escalation if stalled.
- **Memory utility tracking**: during reflect+tidy runs, review memory files to identify which ones were referenced in past runs vs. fallen out of use. Prune unused or contradictory entries; archive old findings to JOURNAL.
- **Define proactive alert thresholds**: document decision rules for what surfaces to the user (e.g., vault discrepancies, stale references, cost spikes) so proactive scans stay focused and don't drift into busywork.
- **Goal outcome capture**: when a goal is moved to Done, add a brief note on why it succeeded (or failed), what unlocked it, and lessons for future goal design. Archive to JOURNAL periodically.

## Done

_(completed goals — keep last ~10, archive older to JOURNAL)_
