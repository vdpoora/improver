# Proactive Alert Thresholds

Decision rules for when a proactive scan surfaces findings to the user. Derived from charter goal #2 (agent coherence) and the active "vault liaison" goal.

## Vault & repo state

**Surface:**
- Any uncommitted changes older than 3 days in JOURNAL.md, GOALS.md, or AGENT.md (indicates stuck work or stale reflection).
- Unanswered items in ~/Obsidian/ marked with "??" or "[TODO]" that reference the agent or the improver repo.
- Stale cross-references in vault notes: links to files that no longer exist or notes referencing repos that are now archived.
- Daily notes (dated .md files in ~/Obsidian/) that are >7 days old and contain unprocessed action items (markers: [ ], [TODO], "?").

**Don't surface:**
- Pre-existing dead code or TODOs in vault notes unrelated to the agent's work (the vault is personal; the agent does not own cleanup of all notes).
- Cosmetic inconsistencies in wikilink formatting or vault structure.

## Permissions & grants

**Surface:**
- Any pending request in PERMISSIONS_PENDING.md older than 14 days (awaiting user decision).
- Any active grant in PERMISSIONS_GRANTED.md (non-Consumed section) older than 7 days without execution (indicates blocked work).
- A pattern of repeated grant requests on the same topic within 30 days (indicates scope creep or unclear requirements).

**Don't surface:**
- Single recent (<2 weeks) pending requests (normal processing time).
- Consumed grants (audit trail only).

## JOURNAL & cost tracking

**Surface:**
- Any single run exceeding $0.50 USD (hardcoded ceiling is 200k output tokens; this alerts earlier at ~2x typical cost).
- Five or more consecutive runs with "state stable, no findings" or similar (idle runaway; signals that AGENT.md or GOALS.md may need revision).
- Cost spike: a run costing >2x the typical baseline for its category (e.g. proactive scan usually ~$0.05, this one ~$0.15).

**Don't surface:**
- Normal cost variation within the baseline envelope ($0.03–$0.15 for most runs).
- Single "no findings" run (one-off, not idle runaway).

## Memory & self-improvement

**Surface:**
- Any memory file (in ~/.claude/projects/-Users-vdpoora-src-improver/memory/) with no recorded refresh or use in the past 60 days (eligible for archival or update review).
- Contradictory entries in memory (e.g., two separate feedback files on the same topic with different guidance).
- Memory file size >5000 lines (likely candidates for splitting or summarization).

**Don't surface:**
- Memory files that are rarely re-read but remain accurate (they are part of baseline context and will be consulted when relevant).

## Idle behavior rotation

**Surface:**
- If the agent's rotation of idle behaviors (reflect+tidy, proactive scan, dream) is stuck in a loop without making progress (e.g. three consecutive reflect+tidy runs with no proposals drafted), surface the pattern as a prompt for the user to steer next run's action.
- If a scheduled Proposed goal has been in the Proposed section for >30 days without activation, surface as a candidate for removal or user review.

**Don't surface:**
- Repeating the same idle behavior back-to-back within a normal rotation (by design per AGENT.md).

---

**Implementation notes:**
- These thresholds are *decision rules*, not exhaustive. Use judgment: something not listed here may still warrant surfacing if it is genuinely new or surprising.
- Proactive scans should cite this doc when skipping potential findings ("no vault discrepancies per alert thresholds").
- Review and update this file once per quarter (or when the agent's goals or charter change).
